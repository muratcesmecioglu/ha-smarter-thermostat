# 🧠⁺ Smarter Thermostat

A sophisticated Home Assistant blueprint that intelligently controls your thermostat based on window/door sensors and weather conditions. This automation helps you save energy by automatically managing your heating system while maintaining comfort in your home. 

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fmuratcesmecioglu%2Fha-smarter-thermostat%2Fblob%2Fmain%2Fsmarter-thermostat.yaml)

## 🎯 Key Features

* **Window-Aware Heating**: Automatically turns off heating when windows are open
* **Weather-Based Control**: Activates winter mode based on outdoor temperature
* **Scheduled Operation**: Integrates with Home Assistant schedules
* **Manual Override**: Includes bypass functionality for temporary control
* **Smart Delays**: Configurable delays to prevent frequent switching
* **Detailed Logging**: Comprehensive logging of all state changes and decisions

## 🔄 Operation Logic

### 1. Normal Operation

The automation enables heating when:

* Schedule is active
* Windows are closed
* Outside temperature is below winter mode threshold

### 2. Bypass Mode Active

When bypass is ON, the automation:

* Ignores schedule settings
* Activates heating if:
  * Windows are closed
  * Outside temperature is below winter mode threshold

### 3. Safety Features

* Immediate heating shutdown when windows open
* Temperature-based activation to prevent unnecessary heating in warmer weather
* Configurable delays to prevent system stress from rapid switching

## 🔧 Installation Guide

### Prerequisites

1. **Create a Window/Door Sensor Group**
  * Combine all your window/door sensors into a single binary sensor group
  * This can be done using a [Binary Sensor Group](https://www.home-assistant.io/integrations/group/#binary-sensor-groups)
2. **Configure Generic Thermostat**
  * Create and configure a generic thermostat with:
    * Hot and cold thresholds
    * Temperature sensor
    * Actuator switch
  * You can follow the [Generic Thermostat documentation](https://www.home-assistant.io/integrations/generic_thermostat/)
3. **Create Schedule Helper**
  * Add a new schedule helper entity
  * Configure your desired heating schedule
  * This will be used to define when heating is allowed to operate
4. **Set Up Bypass Switch**
  * Create an input boolean for the bypass system
  * This will allow manual override of the schedule when needed
5. **Configure Weather Integration**
  * If not already present, add a weather integration
  * Configure it for your location
  * This is needed for temperature-based decisions

### Blueprint Installation

6. **Add Blueprint to Home Assistant**

   [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fmuratcesmecioglu%2Fha-smarter-thermostat%2Fblob%2Fmain%2Fsmarter-thermostat.yaml)

7. **Configure Entities**
  * Select your configured thermostat
  * Choose the weather entity
  * Select the grouped binary sensor
  * Pick your schedule helper
  * Choose the bypass switch
8. **Name Your Automation**
  * Give your automation a meaningful name
  * This will help identify it in logs and the UI
9. **Test the Setup**
  * Verify all entities are correctly selected
  * Test the window sensor response
  * Check schedule functionality
  * Confirm bypass switch operation
10. **Enjoy Your Smart Heating! 🎉**
  * Your smart thermostat automation is now ready
  * Monitor the logbook for operation details
  * Make adjustments as needed

## ⚠️ Additional Notes

* All temperature values can be in either Celsius or Fahrenheit
* Window delay should be kept relatively short (5-10 seconds recommended)
* Winter mode delay should be adjusted based on local climate conditions
* Multiple window sensors can be grouped into a single binary sensor group

## 🔍 Debugging

The automation provides detailed logging of all decisions:

Example:
```
"HEAT mode activated: Schedule ON, Window closed, Temperature 14°C below threshold (16°C)"
"Heating is OFF because: Window is open"
"Heating is OFF because: Temperature (18°C) above threshold (16°C)"
```

## 🤔 Why Another Thermostat Automation?

I couldn't find a blueprint that perfectly matched my use case. Existing blueprints lacked scheduling functionality, which was crucial for my needs. In my home, I run the heating system between 7 AM and 11 PM, and I needed a bypass switch for occasions when continuous operation is required outside these hours.

The main motivations for creating this blueprint were:

* Integration of a flexible scheduling system
* Addition of a bypass switch for manual override
* Combination of window sensors and weather-based control
* Need for detailed logging of system decisions

I decided to share this enhanced blueprint with the community, hoping it would help others who have similar requirements for their heating automation.

## 🧪 Experimental Blueprint

Please note that this is an experimental blueprint, still in the testing phase. While it has been used in my own home, there may be undiscovered issues or edge cases that could affect its reliability.

Use this blueprint at your own risk, and be prepared to monitor its performance closely. I recommend thoroughly testing it in a non-critical environment before deploying it in your production setup.

If you encounter any problems or have suggestions for improvement, please feel free to provide feedback on the original forum post or the GitHub repository. Your input will help make this blueprint more robust and useful for the entire community.

## 🙏 Credits

Based on the original work by Siyez ([Smart Thermostat](https://community.home-assistant.io/t/smart-thermostat-radiator/258368)) and alexbabel's fork ([Smart Thermostat 2.0](https://community.home-assistant.io/t/smart-thermostat-2-0-blueprint/478348)). Modified and enhanced by Murat Çeşmecioğlu. 

## 📝 Changelog

### Version 1.0 (November 11, 2024)

* Initial release
* Core features implemented:
  * Window sensor integration
  * Weather-based control
  * Schedule helper support
  * Bypass switch functionality
  * Configurable delays
  * Detailed logging system

For more information: [🧠⁺ Smarter Thermostat](https://community.home-assistant.io/t/smarter-thermostat/793618)
