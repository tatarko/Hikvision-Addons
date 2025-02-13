# Changelog

## 3.0.0-beta.19 - 2022-04-15

### Added

- Added hangup button
- Changed unlock record attribute for switch relay to "00" when it was empty when using Isapi/... for open door

## 3.0.0-beta.18 - 2022-04-11

### Added

- Added support for DS-HD series?

## 3.0.0-beta.17 - 2022-03-21

### Added

- Testing Alarm input for zones/types
- Changed login method to offline event uploading, preventing backlog om some devices?

## 3.0.0-beta.16 - 2022-03-18

### Added

- Zone alarm device trigger for indoor and outdoor

## 3.0.0-beta.13 - 2022-03-11

### Changed

- Revert `amd64` SDK update

## 3.0.0-beta.10 - 2022-03-11

### Added

- MQTT integration. 
  **Note: requires a running MQTT broker**
- Each doorbell is now visible as a device inside Home Assistant
- New sensors and entities:
  - `Call state` sensor: displays the state of the call (idle, ringing, dismissed)
  - `Buttons` for _accepting_/_rejecting_ the call, _rebooting_ the device
  - `Switches` for controlling the output switches connected to the doorbell unit (to open gates, doors)
  - `Device triggers` for receiving alarm events (motion detection, door not closed, tamper alarm, etc..)
  - Diagnostic `text` entity for testing out ISAPI commands (advanced)
- New configuration option: `output_relays` (to manually specify the number of relays)
- If the add-on has trouble connecting to the doorbells, the sensors show up as `unavailable`

### Changed

- Update documentation, add section about **MQTT** broker installation
- The add-on no longer creates simple `binary_sensor`, but  various entities associated to one or more `device`, each visible in the HA UI
- Update development documentation with overview on software architecture, add `docker-compose.yml` example.
- Update `amd64` SDK to version `6.1.9.4_build20220412`

### Deprecated

- The Home Assistant `REST API` integration is no longer recommended in favor of the `MQTT integration`, and no new features will be added to it

### Fixed

- Sensors no longer disappear on HA restart

## 3.0.0-beta.9 - 2022-03-06

## Fixed

- Quickfix for ISAPI alarm #af214751244b732402375adc6401a1fdd230d15d

## 3.0.0-beta.8 - 2022-03-06

### Changed

- The `door` sensors attribute `Unlock` is a more readable string

### Fixed

- Multiple doorbells no longer conflict with their sensor names #18

## 3.0.0-beta.7 - 2022-03-06

### Added

- Changed sensor 'off' state to 5 sec instead of 1 for testing
- Added ISAPI alarm
- Added alarm sensor for 'door not open/closed' alarm
- Added Face Access Terminal as supported device

## 3.0.0-beta.1 - 2022-02-23

This is the first of the releases made available under the __Beta channel__. Expect some small issues while we iron out the last bugs and get ready for an exiting official release!
You feedback is very welcome! If you have any doubt, would like to report a bug or to simply chime in, please have a look at the [Github Issues page](https://github.com/pergolafabio/Hikvision-Addons/issues) and drop us a note!
Now let's move on to __what's new__:

The addon has been completely __overhauled__, with lots of __new features__ and an __improved codebase__ that will aid future integrations and improvements.

### Added

- Handle __multiple doorbells__
    - Customize the __name__ of each doorbell
    - __Command__ each device separately (open door, reboot, etc...)
- Run the addon as a standalone __Docker container__, for Home Assistant installations without _supervisor_. (this feature is considered _experimental_ and still to be appropriately tested. Feedback is welcome!)
    - Load __configuration__ from a JSON/YAML file or from environment variables
- Configurable __system logs__
- Events coming from the doorbells are written to the __console__, for easier debugging and troubleshooting
- Automated __testing__ and __release__ using Github Actions
- New __beta channel__ to test pre-release versions of the addon
- Add basic __blueprint__ to showcase how to integrate the sensors inside HA

### Changed

- Change the name of the addon to __Hikvision Doorbell__
- Improved __documentation__ for both end users and developers
- Changed the format of __input commands__ to: `<command> <doorbell_name> <optional_argument>`
  - The __name__ of the doorbell must be specified as part of the command
- Changed the sensors created inside HA by this add-on:
  - The doorbell name is part of the sensor name
  - Sensors are initialized to `off` __on startup__
  - Sensors are __`binary_sensors`__
  - Define __`device_class`__ for each sensor

### Deprecated
- Old __configuration options__
- Remove __`aarch64`__ folder of the deprecated addon
