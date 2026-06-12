# Polaris: Safety App

> It is not a button you press when you are scared. It is a system already running before the danger begins.

---

## Overview

Polaris is a passive, always-on personal safety companion built with Flutter and Firebase. Unlike every existing safety application, Polaris requires no interaction when it matters most. It runs silently in the background, adapting across three intelligent modes (Walk/Run, Drive, and Idle) each calibrated to the specific risks of that situation.

Every existing safety app fails for the same reason. They are reactive. They require you to unlock your phone, open the app, and manually trigger an alert. In a genuine emergency, that assumption fails completely. A car crash happens in 200 milliseconds. Someone following you does not announce themselves. Polaris acts before you have the chance to react.

---

## Innovation Category: Edge-First with AI-Native components

Critical safety features run entirely on-device with zero cloud dependency. TFLite sound classification, accelerometer crash detection, and Google Activity Recognition API all process data locally. This means Polaris functions even with no signal — exactly when and where safety matters most. Intelligence is not a feature layer added on top. It is the core mechanism driving mode detection, threat classification, danger scoring, and escalation logic.

---

## The Problem

- Existing apps require manual interaction — useless in a real emergency
- They are obvious to use — opening a safety app in front of a threat is dangerous
- They do one thing — send an alert — with no escalation, no intelligence, no context
- False alarms cause alert fatigue, so contacts stop responding seriously
- They fail in low signal areas exactly when they are needed most
- There is no app that watches your environment for you and acts before you react

---

## The Solution

Polaris operates across three intelligent modes from the moment a session begins. The user sets it once and the app takes over completely.

**Walk and Run Mode**: monitors route, movement speed, and ETA in the background. Any deviation from the planned path, unexpected stop, or missed check-in triggers the escalation ladder automatically. No phone interaction needed after session start.

**Drive Mode**: monitors for crash signatures via accelerometer, tracks route deviation, and supports ride-share passenger safety. Alerts escalate through the phone and optionally through Bluetooth car speakers or Android Auto display.

**Idle Mode**: monitors ambient sound passively via an on-device TFLite classifier, keeps the check-in timer active, and listens for silent SOS triggers when the user is stationary somewhere unfamiliar or uncomfortable.

At any point, regardless of active mode, a triple volume press or sharp shake silently activates SOS. From that moment the evidence locker begins recording, GPS logs continuously, and the escalation ladder activates.

---

## Target Audience

- Young women commuting or walking alone at night
- University students traveling between campus and accommodation
- Late night workers and shift commuters with recurring vulnerability windows
- Long distance and late night drivers at risk of fatigue related incidents
- Travelers and newcomers navigating unfamiliar cities
- Parents and emergency contacts who form the coordinated response network

---

## Core Features

### Safety Circle
Trusted contacts see live status badges in real-time (Safe, Walking, Driving, Idle, Needs Check-in). Location sharing with visibility controls — full location, area only, or status only. Circle invites via QR code or shareable link. Ghost mode for temporary invisibility. Scheduled sharing activates location only during set hours. Emergency contacts outside the circle as a backup escalation layer.

### Walk and Run Mode
Journey mode with destination and ETA tracking running entirely in the background. Route deviation alert fires if the user strays from the planned path. Unfamiliar zone awareness via geofencing activates heightened monitoring when the user leaves known areas. Low battery warning notifies the circle automatically when battery drops below 15 percent during an active session. Last known location saves final GPS coordinates to Firebase if the phone dies mid-journey.

### Drive Mode
Crash and impact detection via accelerometer and gyroscope fusion detects sudden violent deceleration consistent with a vehicle collision. A 10-second cancel window fires before any alert reaches contacts. Journey mode and route deviation monitoring apply identically to Drive Mode. Ride-share passenger mode allows the user to log the driver name, plate number, and destination before getting in — the circle sees this information live. Check-in confirmation via car screen tap through Android Auto or paired Bluetooth removes any need to touch the phone while driving.

### Idle Mode
Ambient sound detection via on-device TFLite classifier monitors for threat-pattern audio including screaming, glass breaking, and aggressive confrontational sounds. Silent SOS via triple volume press or sharp shake gesture. Check-in timer with dead man's switch remains active throughout — periodic silent vibration asks if the user is safe, escalation begins if no response within 60 seconds.

### Escalation and Response
Two silent on-device check-ins fire before any contact is notified, handling the majority of false alarms without involving anyone. If both go unanswered, two or three primary circle contacts receive a low urgency alert with live GPS — contacts can claim the alert so the response is coordinated. If contacts do not confirm safety, silent auto-SOS activates simultaneously with mode-specific threat detection. The evidence locker begins recording instantly. If the user remains unresponsive and confirmed danger signals are detected, emergency services are contacted automatically with coordinates and the evidence locker record attached.

### Maps and Community
Live map with avatar pins for all circle members. Safe and time-aware routing suggests the safest path based on community danger reports, time of day, and crowd density — not just the shortest route. Crowdsourced danger heatmap aggregates anonymous community-reported unsafe zones with time-decay so old reports expire automatically. Safe spots layer shows community-pinned locations including pharmacies, police stations, and well-lit areas. Crowd density layer shows estimated foot traffic by area and time so users know whether a location is populated or isolated before entering. Live community alert pins show real-time reported incidents across the map.

### Evidence Locker
Every session is permanently logged in Firebase. Full GPS trail with timestamps. Audio recordings triggered during the session stream in real time to Firebase Storage. Silent photo capture activates on SOS trigger and uploads instantly — not saved locally where it could be deleted. All evidence is cloud-locked, tamper-proof, and cannot be removed from the device. Legally significant and unique to Polaris.

---

## Bonus Features

**Drowsiness Detection**
Front camera monitors blink rate, eye closure duration, and head drop angle while driving using Google ML Kit face mesh. When a sustained fatigue pattern is detected, an escalating alert fires through the phone, then Bluetooth car speakers, then the Android Auto display simultaneously.

**Sign Language SOS Gesture**
Deaf and mute users can trigger SOS through a recognized hand gesture detected by the front camera using on-device TFLite. No voice, no touch, no visible interaction required. Strengthens accessibility and SDG 10 alignment.

**Voice Keyword Trigger**
User sets a custom safe word during onboarding. When the microphone detects it, SOS fires silently. Completely covert, no visible interaction needed.

**Smartwatch Integration**
One-tap SOS button on any paired smartwatch silently activates SOS when the phone is inaccessible. Haptic feedback on the watch confirms the alert was sent.

**Gait Analysis**
Learns the user's movement baseline for walking and running separately over time. Flags sudden stops, asymmetric dragging patterns, and fall detection passively via accelerometer without any user input.

**Medical Emergency Detection**
Accelerometer detects collapse or seizure patterns post-fall. Users with flagged medical conditions stored in their profile trigger faster escalation directly to emergency services with medical information and live location attached.

**Driving Behavior Scoring**
Post-trip safety score generated from accelerometer and GPS data — hard braking, sharp cornering, sudden acceleration, average speed. No external hardware required. Feeds back into crash detection model accuracy over time.

**Bystander Mode**
A nearby stranger can scan a QR code displayed on the lock screen to access a limited emergency view — name, emergency contacts, and last known location — without needing the app installed.

---

## Technology Stack

### Frontend
**Flutter and Dart**


### Backend
**Firebase**: API-First architecture via Firebase REST and Realtime APIs
**Cloud Functions**: server-side escalation logic and check-in timer triggers


### Data Layer
**Firebase Realtime Database**: live safety circle status and GPS sync
**Firestore**: user accounts, session history, heatmap reports, circle relationships
**Firebase Storage**: audio recordings, photo evidence, GPS trail logs
**Firebase Auth**: phone number authentication


### AI and Edge Components
**Google ML Kit**: face mesh for drowsiness detection
**TensorFlow Lite**: on-device sound classification and sign language gesture recognition
**Google Activity Recognition API**: on-device mode detection via built-in phone sensors
**sensors_plus**: accelerometer and gyroscope for crash detection and gait analysis


### Key Packages
flutter_background_service, geolocator, flutter_background_location, flutter_volume_controller, record, camera, flutter_contacts, google_maps_flutter, flutter_activity_recognition, battery_plus, permission_handler, flutter_local_notifications, flutter_blue_plus, go_router, provider

---
