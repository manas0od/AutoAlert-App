# AutoAlert 🛺

**Bridging life, connecting services.**

AutoAlert is a low-cost IoT system that lets customers summon an auto-rickshaw
driver who has briefly stepped away from their stand. A physical call button
mounted on the vehicle sends a real-time push notification to the driver's
phone — from anywhere with internet, not just when near the vehicle.

## The Problem

Auto-rickshaw drivers in Kerala often park at a stand but aren't always
sitting in the vehicle — they step away for tea, a break, or a quick
conversation. Customers arriving at an empty-looking stand have no way to
signal that they need a ride.

## How It Works

1. Customer presses the illuminated button on the auto-rickshaw.
2. An ESP8266 microcontroller sends a push notification over the internet
   (via [ntfy.sh](https://ntfy.sh), a free, public notification relay).
3. The driver's phone receives an instant alert — with **Coming** / **Busy**
   reply actions right in the notification.
4. The driver's reply is sent back to the device, lighting a green or red
   LED so the customer gets visual confirmation without needing a smartphone.

## Why This Architecture

- **No cloud backend, no Firebase, no company-owned database.** Pairing
  credentials (hashed) and configuration live only on the ESP8266's own flash
  memory. Zero recurring cost, zero third-party data exposure.
- **ntfy.sh** is used purely as a public message relay — no account, login,
  or payment required.
- The device makes only outbound network requests; it never accepts
  unsolicited inbound connections.

## Tech Stack

- **Firmware:** C++ (Arduino framework) on a NodeMCU ESP8266 V3
- **App:** Native Android — Kotlin + Jetpack Compose, Room database,
  glassmorphic UI
- **Notifications:** ntfy.sh (self-hosted-compatible, open protocol)
- **Hardware:** ESP8266, illuminated push button, 2x status LEDs, 18650
  Li-ion battery, TP4056 charging module, boost converter

## Status

This is a working prototype built for a school science fair. Core flow
(button press → notification → reply → LED confirmation) is tested and
functional. See the [project report](./AutoAlert_Project_Report.docx) for
full technical documentation, including challenges faced and future scope
(WiFi self-provisioning, iOS support, remote battery monitoring, and more).

## Images

<img width="720" height="1650" alt="Image" src="https://github.com/user-attachments/assets/4a312f39-7e52-47b9-8c70-e206937e3b00" />
<img width="720" height="1369" alt="Image" src="https://github.com/user-attachments/assets/c54ad656-eff2-4cb5-80c9-8ec609f91a27" />

## Author

Manas O D
