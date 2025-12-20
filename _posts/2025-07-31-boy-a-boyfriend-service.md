---
title: "Relationship Services, Inc. — Buy-a-Boyfriend Service™"
date: 2025-07-31
categories: fun-things
tags:
  - twilio
  - voice-flows
  - creative-tech
  - bad-ideas-that-worked
---

I wanted to ask my girl out.

I built a fake telemarketing company, printed business cards, bought a phone number, and designed a fully scripted interactive voice experience that let her *purchase* a boyfriend.

This page documents the project, the tech behind it, and the most important outcome: **she said yes**.

---

## **The Setup**

I designed business cards for a fictional company:

**Relationship Services, Inc.**
*Buy-a-Boyfriend™ Division*

The front looked corporate and legitimate.
The back had a phone number ending in `-luv-u`.

If you called it, something happened.

---

## **The Card**

![Business Card Front](/assets/images/bidnesscard.png)


---

## **Initial Plan (Abandoned)**

My first instinct was to spin up my own server to handle calls directly.

That failed for two reasons: Phone call handling is annoying. I wanted fast iteration and branching logic, not a weekend fighting SIP. So I pivoted.

---

## **The Actual Implementation**

I used Twilio and its flow-based call system and I did not have to build a custom back-end.

This let me:

* Buy a real phone number
* Handle incoming calls
* Branch logic based on keypad input
* Play hosted MP3s
* Inject recorded voice lines at key moments

---

## **Call Flow Overview**

![Call Flow Diagram](/assets/images/phoneservice.png)

High-level flow:

1. Call arrives
2. Corporate greeting
3. Menu of “boyfriend options”
4. Comedy rejection paths
5. One real option
6. Recorded personal message
7. The actual question

---

## **The Script**

> *At Relationship Services, Inc.’s Buy-a-Boyfriend™ Service, we offer curated romance solutions from our exclusive catalog. This is a high-priority case. Please listen carefully, as today’s top matches are limited-time offers.*

### **Option 1**

**Maluma**
Colombian pop star.
Six-pack included.
Possibly too sexy.
Already has a daughter.
Lives a busy, famous-person life.

Outcome:

> *Excellent choice. Malumaa will serenade you nightly — when he’s not on tour.*
> *Unfortunately, his tour schedule is booked until 2057, and he’s emotionally unavailable until further notice.*

---

### **Option 2**

**Ricky Martin**
Living la vida loca since the 90s.
Recently declared he would go hetero exclusively for you.
Bonus: joint ownership of a dance studio.

Outcome:

> *Ricky is sold out. Please try another option.*

---

### **Option 3**

**Su-mer-say**
Full-time admirer.
Aspiring boyfriend.
Thinks you invented sunlight.
Claims a Caribbean mermaid once saved his life.

This one worked.

---

## **She picked me :3**

After selecting Option 3, the system switches tone.

> *Congratulations. You’ve selected the Su-mer-say Boyfriend Ultra Deluxe Package.*
> *Su-mer-say is committed to providing emotional support, affection, constructive criticism, accountability, and lots of love.*

Then the flow pauses.

A **recording of my voice** plays.

That’s where I ask her to be my girlfriend.

---

## **If She Says Yes**

> *Processing your request…*
> *Item added to cart: 1 Su-mer-say (Boyfriend Edition)*
> *Cart total: 1 billion trillion dollars.*

> *Applying promo code: TRUELOVE*

> *Congratulations! Your transaction is complete.*

> *As part of your premium subscription, your new boyfriend will be adding you to the family Spotify account shortly. Please be sure to accept the invitation.*

> *Your first date is scheduled for Saturday, August 2nd, in the afternoon, in the city.*

A song plays.

---

## **Closing Message**

> *Thank you for choosing Relationship Services, Inc., where feelings come first and shipping is always free.*
> *Love is non-refundable, but highly customizable.*
> *Goodbye.*

---

## **What I learned**

* Voice UX design
* State-based logic


Emotionally, it was a gamble.

It paid off.

---

## **Final Outcome**

She said yes.

The service was immediately retired.

One day Ima marry this girl.

---