# Maxxfan Contract for ESPHome

This package now includes an implementation for [brown-studios/esphome-maxxfan-protocol](https://github.com/brown-studios/esphome-maxxfan-protocol), so heater support works out of the box. You do **not** have to implement your own remote or scripts—everything works out of the box for standard operation.

## What this package provides

- A fan card which implements the contract
- Min/max speeds to clamp the set speed
- Ceiling mode
- Air in/out modes
- A contract for how your scripts should trigger transmissions

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
