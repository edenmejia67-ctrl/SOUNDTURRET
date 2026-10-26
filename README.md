# Sound Sentry – 3D Circuit Simulator

An interactive 3D simulator of **Sound Sentry**, an ESP32-based smart noise monitor. It shows the breadboard wiring, lets you click each part to see what it does, and simulates a classroom where noise rises and falls so you can watch the LEDs, buzzer and laptop log react.

> **Note:** All sensor values in this simulator are **simulated**. Use real trial data from the physical device for any paper or analysis.

## Live demo

After you enable GitHub Pages (see below), the simulator will be at:

`https://<your-username>.github.io/<repo-name>/`

## Run it locally

No build step and no dependencies to install. Open `index.html` in a modern browser (Chrome, Edge, Firefox or Safari).

It loads [three.js r128](https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js) from the cdnjs CDN, so you need an internet connection the first time you open it.

## Features

- Orbit, zoom and click-to-inspect 3D scene of the breadboard, ESP32, microphone, SD module, LEDs and buzzer
- **Pretest (manual)** vs **Posttest (Sound Sentry)** modes to compare noticing noise by ear against detection by the device
- Adjustable room noise (30–100 dB) and warning threshold (50–85 dB), plus an auto scenario of students talking
- Fault simulation: blocked microphone and missing SD card
- Laptop screen view showing the live CSV log and a noise chart
- **Export CSV** of the logged readings (`time_s,db,status`)
- Light and dark theme that follows your system setting

## Controls

| Action | How |
| --- | --- |
| Rotate | Drag |
| Zoom | Mouse wheel / trackpad scroll |
| Part info | Click a part |
| Look at the laptop screen | Click the laptop or press **Laptop view** (`Esc` to leave) |
| Reset camera | **Reset view** |

## Wiring (as shown in the simulator)

| Part | Connection |
| --- | --- |
| MAX4466 microphone | VCC → 3V3, GND → GND, OUT → GPIO34 (ADC1) |
| MicroSD module | VCC → 5V, GND → GND, CS → GPIO5, SCK → GPIO18, MISO → GPIO19, MOSI → GPIO23 (card formatted FAT32) |
| Green LED (quiet) | GPIO25 → 220 Ω resistor → GND |
| Yellow LED (caution) | GPIO26 → 220 Ω resistor → GND |
| Red LED (warning) | GPIO27 → 220 Ω resistor → GND |
| Active buzzer | GPIO32 → buzzer → GND |

The ESP32 is powered over USB. The MAX4466 is not calibrated, so the dB value is an estimate unless checked against a sound level meter.

## Deploy with GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose the `main` branch and the `/ (root)` folder, then save.
4. Wait a minute or two, then open the URL shown at the top of the Pages settings.

## Project structure

```
.
├── index.html   # the whole simulator (HTML, CSS and JavaScript)
└── README.md
```
