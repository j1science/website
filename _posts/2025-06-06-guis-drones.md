---
title: "Grid & Crop Tooling for Processing Drone Imagery"
date: 2025-02-12
categories: my-research
tags:
  - geospatial
  - gdal
  - tkinter
  - geotiff
  - shapefile
  - drone-imagery
---

## Overview

This project consists of two tightly related Tkinter desktop GUIs for working with large GeoTIFFs, particularly drone-derived orthomosaics. One tool is a GeoTIFF grid builder and labeling application focused on structure, geometry, and reliable export of spatial data, while the other is a lightweight orthomosaic viewer and cropper optimized for navigation, inspection, and fast extraction of native-resolution subsets. They are intentionally kept separate to avoid overloading a single interface, and together they cover the manual geospatial tasks I found myself repeating most often.

Tool 1, the GeoTIFF Grid Builder, is designed for structure and export: it loads and preprocesses GeoTIFFs, displays them using a multi-resolution image pyramid, draws real-world-sized and rotated grids, labels grid cells using serpentine logic, and exports the resulting geometries as ESRI Shapefiles. Tool 2, the Orthomosaic Viewer and Cropper, is optimized for navigation and extraction: it enables smooth panning and zooming of massive rasters, displays both pixel and map coordinates, and exports the current viewport as a native-resolution GeoTIFF while preserving the original CRS, geotransform, and nodata values. Both tools share the same design philosophy—native GDAL reads and writes, minimal GIS dependencies, desktop-first mouse-driven interaction, and explicit safeguards around coordinate reference systems and pixel geometry.

![Animated GIF showing grid workflow](/assets/images/grid.gif)


![Animated GIF showing cropper workflow](/assets/images/cropper.gif)

---

## Tool 1: GeoTIFF Grid Builder


### What this tool is

A **Tkinter desktop application** for loading GeoTIFF imagery, preprocessing it into a clean, validated TIFF, displaying it efficiently, drawing configurable grids, labeling cells, and exporting those grids as shapefiles.

It is meant for:

* Plot grids
* Experimental layouts
* Structured sampling
* Any situation where grid geometry must match real-world dimensions

---

### Primary Workflow (End-to-End)

1. **Launch**

   * Run `main.py`
   * A Tkinter window opens and instantiates `GeoTIFFApp` from `app.py`

2. **Open & Pre-process TIFF**

   * Click **“Open & Pre-process TIFF”**
   * A guided wizard runs in the background:

     * Reads the input GeoTIFF
     * Optionally strips alpha bands
     * Optionally downsamples large images
     * Writes a cleaned `_clean.tif`
     * Builds a multi-level PIL image pyramid
     * Runs a full block-by-block integrity check
     * Displays a preview
     * Enables **“Load in Viewer”** only if validation passes

3. **Load into Viewer**

   * Spatial metadata is read:

     * CRS
     * Units
     * Geotransform
   * Projection details appear in the sidebar
   * Warnings are shown for geographic CRS (degrees)
   * The image pyramid is rendered to the canvas

4. **Grid Creation**

   * Double-click to set the grid anchor point
   * Configure:

     * Rows / columns
     * Cell size
     * Spacing
     * Rotation
   * Draw the grid on the canvas

5. **Labeling & Export**

   * Generate serpentine numbering based on:

     * Start corner
     * Direction
     * Prefix
   * Export grid polygons as a shapefile with attributes

---

### UI Layout & Controls

**Main Window (widgets.py)**

* Fixed-width left sidebar with collapsible sections
* Right-side canvas with scrollbars
* Bottom status bar for warnings and messages

**Menus**

* **TIFF**

  * Launch preprocessing wizard
  * Pyramid level slider
* **Grid**

  * Draw / reset grid
  * Grid parameter controls
* **Numbering**

  * Start corner & direction
  * Start number and prefix
  * Generate / reset numbering
  * Export shapefile

**Canvas Interactions**

* Double-click: set anchor
* Arrow keys: nudge anchor
* Mouse wheel: change pyramid level

---

### Core Modules

* `main.py` — Minimal entry point
* `app.py` — App bootstrap and wiring
* `wizard.py` — Background preprocessing workflow + UI logging
* `widgets.py` — Tkinter layout and menu wiring

---

### Services & Responsibilities

* **preprocess.py**

  * Reads GeoTIFF via GDAL
  * Strips alpha bands
  * Downsamples if needed (default ~100 MB target)
  * Writes cleaned TIFF
  * Generates display pyramid

* **check_tiff_integrity.py**

  * Reads every block of every band
  * Ensures the output TIFF is fully readable

* **metadata.py**

  * Parses CRS and geotransform
  * Computes pixel sizes (meters where possible)
  * Handles pixel ↔ geographic coordinate conversion

* **image.py**

  * Manages pyramid levels
  * Maintains scale factors
  * Renders the active display image

* **grid.py**

  * Stores anchor and grid geometry
  * Converts feet → pixels correctly
  * Draws rotated grid polygons
  * Generates serpentine numbering

* **export.py**

  * Writes ESRI Shapefiles
  * Fields: `area_name`, `name`, `area`, `gid`
  * Writes UTF-8 `.cpg`
  * Optional WGS84 support

---

### Notable Safeguards

* Explicit warnings for geographic CRS
* Axis-specific pixel size handling (non-square pixels)
* Block-level TIFF validation before display
* No silent assumptions about units or projections

---

## Tool 2: Orthomosaic Viewer & Cropper

![Animated GIF showing cropper workflow](/assets/images/cropper.gif)

### What this tool is

A **small, self-contained GeoTIFF viewer and cropper** for very large orthomosaic rasters.

It is optimized for:

* Fast pan/zoom
* Inspecting specific regions
* Exporting exact viewport crops at **native resolution**

---

### What it does

* Opens large orthomosaic GeoTIFFs
* Builds `.ovr` overviews when missing
* Renders the visible window to a Tkinter canvas
* Supports:

  * Mouse drag panning
  * Mouse wheel zooming
* Displays:

  * Pixel coordinates
  * Map coordinates
* Exports the current view via `gdal.Translate`

  * Uses `srcWin`
  * Preserves CRS, geotransform, nodata
  * Always exports **full-resolution data**

---

### Entry Points

The logic is intentionally duplicated with different defaults:

* `main.py`

  * Primary viewer
  * Extra startup logging
  * Default: `Orthomosaic.data.tif`

* `hort.py`

  * Same GUI logic
  * Cleaner startup
  * Default: `Orthomosaic.data.tif`

* `hort_cropper.py`

  * Same GUI logic
  * Default: `Orthomosaic.data_HFII.tif`

---

### Launchers

* `run_ortho_cropper_gui.sh`
* `run_hort_cropper_gui.sh`

Both:

* Launch the GUI
* Log stdout/stderr to desktop/home
* Surface GDAL errors cleanly

---

### Display & Export Details

* Non-uint8 rasters are normalized for display

  * Percentile stretch (1–99%)
* Export always uses:

  * Original data type
  * Native resolution
  * Original projection

---

## Data & Environment

**Dependencies**

* Python
* tkinter
* Pillow
* numpy
* GDAL / OGR / OSR (`osgeo`)

**Environment**

* Conda environment noted as `geotiff_env`

**Data Directories**

* `ROUTINE_IN`, `TEST_IN` — input GeoTIFFs
* `ROUTINE_OUT`, `TEST_OUT` — exported shapefiles and crops

---

