# RadioBeat

**Watching your heartbeat through the air, using only WiFi.**

A contactless heart-rhythm monitor built for Qutuhal InnovateX 2.0 (Grade 9, Frontier Innovators).

**Live site:** https://adhvi29.github.io/radiobeat/

By **Adhvik Mahesh** — Grade 9, Global Indian International School (GIIS), Dubai
📧 [adhvikmahesh29@gmail.com](mailto:adhvikmahesh29@gmail.com)

## The problem

A dangerous irregular heartbeat called **atrial fibrillation (AFib)** makes the heart beat unevenly. That lets blood sit still inside the heart and form a clot, and if the clot reaches the brain it causes a stroke.

It is usually preventable, because a doctor can prescribe medicine that stops those clots forming. The problem is that most people never find out they have it. AFib is often silent, it comes and goes, and it tends to show up at night while you are asleep. Every device that could catch it, like a smartwatch or a chest strap, has to be worn, and that is exactly what people take off at bedtime.

## The idea

Every time your heart beats, your chest moves a tiny amount. That movement changes the way WiFi signals travel across a room. RadioBeat uses two ordinary ESP32 WiFi chips, one transmitting and one listening, and reads the Channel State Information (CSI) to recover that movement.

The hard part is that breathing moves the chest around 5 mm while a heartbeat moves it less than 0.5 mm, so the heartbeat is buried underneath. Breathing and heartbeats happen at different rates, though, so a band-pass filter can separate them:

| Signal | Frequency | What happens to it |
| --- | --- | --- |
| Breathing | 0.2 – 0.4 Hz | Filtered out |
| Heartbeat | 0.8 – 2 Hz | Kept |

## Hardware

| Part | Role |
| --- | --- |
| ESP32-WROOM-32E | Transmitter, sends a steady WiFi signal |
| M5StickC Plus2 (ESP32) | Receiver, captures CSI |
| Laptop | Signal processing and web dashboard |

About $20 of parts in total.

## Build progress

- [x] **Week 1** — Problem statement and research
- [ ] **Week 2** — Two nodes talking *(in progress: transmitter broadcasting, receiver locking on at −34 dBm; CSI capture underway)*
- [ ] **Week 3** — Breathing detection
- [ ] **Week 4** — Heartbeat extraction
- [ ] **Week 5** — Irregular-rhythm alert
- [ ] **Week 6** — Validation and demo

## What it can and cannot do

**It can** notice when beat-to-beat timing turns irregular, track breathing rate overnight, run in the dark with nothing worn, and prompt someone to go and get checked.

**It cannot** replace an ECG. An ECG measures the heart's electrical signal through electrodes, while RadioBeat senses movement, so there is no P wave to record. It cannot diagnose anything, it does not cope well with a busy room, and it currently follows only one person at a time.

It is a prompt to go get checked, not a verdict.

## About this site

`index.html` is a self-contained page with no build step and no dependencies. The live console is a **simulation** of what the finished system is intended to reconstruct, not a recording from live hardware.

---

⚠️ **Not a medical device.** A student project and concept demonstration only. Not intended for diagnosis, treatment, or any clinical use.
