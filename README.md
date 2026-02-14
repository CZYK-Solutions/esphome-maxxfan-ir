# Maxxfan IR for ESPHome

This package enables full control of your Maxxfan smart fan from Home Assistant using ESPHome. It implements the Maxxfan IR protocol, including heater support, out of the box.

A default remote is provided based on [brown-studios/esphome-maxxfan-protocol](https://github.com/brown-studios/esphome-maxxfan-protocol), covering all standard Maxxfan functions. Custom remotes are optional if you wish to extend or override the default behavior.

## What this package provides

- Full Maxxfan IR protocol support, including heater functionality, out of the box
- Home Assistant fan card integration with:
    - Speed control: 1–10 (mapped to 0%–100% of the fan’s speed range, excluding 90%)
    - Direction control: Intake (reverse) and Exhaust (forward)
    - Lid control: Closed (oscillation off) and Open (oscillation on)
- Configurable minimum and maximum fan speeds for clamping automation or manual control

## Notes

- Setting the fan card speed to 0 turns the fan off.
- Speeds 1–10 on the fan card correspond to 0%–100% of the fan’s speed range (excluding 90%).
- Speed 1 can be used to open the lid without ventilation.
- The actual speed is limited by the `min_speed` and `max_speed`.
- Speed clamping is useful, for example, if you automate the fan based on an external CO₂ sensor and want to prevent the fan from exceeding a certain speed or toggling on/off while sleeping.

## How to use this package

1. Add this package to your ESPHome device YAML:

```yaml
packages:
  fan: github://CZYK-Solutions/esphome-maxxfan-ir/esphome.yaml
```

---

## Troubleshooting

- If a button does not work, ensure your IR LED is positioned for clear line-of-sight to the fan's receiver.
- For protocol issues, consult the [brown-studios/esphome-maxxfan-protocol](https://github.com/brown-studios/esphome-maxxfan-protocol) documentation.

---

## Example Hardware

- ESP32-S3 (e.g., M5 Atom Lite S3)

## Coffee?

If you find this project useful, consider buying me a coffee to support further development!

<a href="https://www.buymeacoffee.com/czyk" target="_blank">
  <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" height="40">
</a>
