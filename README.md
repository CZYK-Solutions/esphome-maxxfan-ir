# Maxxfan Contract for ESPHome

This package defines a contract for controlling a Maxxfan via using ESPHome. It provides expected script IDs, but **does not** configure hardware pins or IR codes. You must implement the `remote_transmitter` and scripts yourself, following the contract described below.

## What this package provides

- A fan card which implements the contract
- Min/max speeds to clamp the set speed
- Ceiling mode
- Air in/out modes
- A contract for how your scripts should trigger transmissions

## What you must implement

You are responsible for:
- Defining the `remote_transmitter` component in your ESPHome config
- Implementing (extending) scripts for each required action, using the correct script IDs
- Providing the correct IR codes for your Maxxfan model

## Example: Minimal Implementation

Below is a minimal example of how to implement the required `remote_transmitter` and scripts in your own ESPHome YAML file:

```yaml
remote_transmitter:
  pin: GPIO4
  carrier_duty_percent: "33%"
  non_blocking: true

script:
  - id: fan_open
    mode: single
    then:
      - remote_transmitter.transmit_raw:
          code: [<YOUR IR CODE FOR OPEN>]
          carrier_frequency: 38kHz

  - id: fan_close
    mode: single
    then:
      - remote_transmitter.transmit_raw:
          code: [<YOUR IR CODE FOR CLOSE>]
          carrier_frequency: 38kHz

  # Add scripts for air in/out at each speed as needed
```

## How to use this package

1. Add this package to your ESPHome device YAML:

```yaml
packages:
  maxxfan_ir: github://CZYK-Solutions/esphome-maxxfan-ir/esphome.yaml
```

2. Implement the `remote_transmitter` and all required scripts in your device YAML, as shown above.
3. Make sure each script uses the correct script ID as defined by the contract (see the package for all required IDs).
4. Provide the correct IR codes for your Maxxfan model.

## Notes

- The package does **not** include hardware pin assignments or IR codes. You must provide these.
- The IR transmitter should use a 38 kHz carrier and 33% duty cycle.
- You can use a tool like Flipper Zero to capture your Maxxfan's IR codes.

---

## Troubleshooting

- If a button does not work, check that the corresponding script exists and uses the correct IR code.
- Ensure your IR LED is positioned for clear line-of-sight to the fan's receiver.

---

## Example Hardware

- ESP32-S3 (e.g., M5 Atom Lite S3)

## Coffee?

If you find this project useful, consider buying me a coffee to support further development!

<a href="https://www.buymeacoffee.com/czyk" target="_blank">
  <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" height="40">
</a>
