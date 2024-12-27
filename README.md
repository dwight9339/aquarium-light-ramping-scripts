# Aquarium Light Ramping Scripts

This repository contains Home Assistant YAML scripts for creating smooth, natural light transitions in your aquarium. These scripts are designed to simulate sunrise and sunset effects, improving the visual appeal of your aquarium while providing a more natural environment for your fish and plants.

## Setup Guide
1. Prerequisites

    A Home Assistant setup with a compatible LED controller.
    Access to your light's entity ID in Home Assistant (found under Developer Tools > States).

2. Adding the Scripts

    Navigate to Settings > Scripts in Home Assistant.
    Create a new script and switch to YAML mode.
    Copy the code for the desired ramping script from this repository.
    Update the entity_id with the ID of your light.

3. Testing the Script

    Run the script manually from the Home Assistant UI to ensure it works as expected.

4. Automating the Ramps

    Use Home Assistant Automations to call the ramp scripts at specific times:
        Example: Call the ramp-up script at 8 AM for sunrise.
        Example: Call the ramp-down script at 8 PM for sunset.

```
alias: Trigger Ramp-Up
trigger:
  - platform: time
    at: "08:00:00"
action:
  - service: script.turn_on
    target:
      entity_id: script.aquarium_ramp_s_curve
    data:
      variables:
        direction: "up"

alias: Trigger Ramp-Down
trigger:
  - platform: time
    at: "20:00:00"
action:
  - service: script.turn_on
    target:
      entity_id: script.aquarium_ramp_s_curve
    data:
      variables:
        direction: "down"
```

## Ramp Shape Playground
I've created a [playground](https://www.desmos.com/calculator/vqs9qccxtg) with interactive graphs for each of the available ramp shapes to help dial in the best lighting schedule. 
![ramp_shape_playground_screenshot(1)](https://github.com/user-attachments/assets/3ca96f93-9ad0-457e-9949-47ad255f9460)

## Contributing
Contributions are welcome! If you have ideas for improving the scripts or want to add new features:
- Submit a pull request with your changes.
- Include a detailed description of the feature or improvement.

## Support

If you encounter any problems, feel free to create an Issue. Please provide details about the problem, including your setup and any error messages.
