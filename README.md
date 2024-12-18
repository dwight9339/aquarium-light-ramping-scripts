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

## FAQ
- Q: Which curve should I use?

    Sine Curve: Best for natural-looking sunlight transitions and plant growth.
    S-Curve: Great for perceptually smooth ramps and algae control.

- Q: What if my lights don't respond correctly?

Ensure the entity_id in the script matches your light's ID in Home Assistant. If you’re still having issues, create an Issue on this repo.
Contributing

We welcome contributions! If you have ideas for improving the scripts or want to add new features:

    Fork the repository.
    Submit a pull request with your changes.
    Include a detailed description of the feature or improvement.

## Support

If you encounter any problems, feel free to:

    Create an Issue: Provide details about the problem, including your setup and any error messages.
    Check the Discussions: Join the conversation to get help or share your ideas.

License

This project is licensed under the MIT License, so feel free to use and modify it for your aquarium setup.
