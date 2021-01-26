# ans_role_config_video_drivers

Install and configure video card drivers.

[![Release](https://img.shields.io/github/release/digimokan/ans_role_config_video_drivers.svg?label=release)](https://github.com/digimokan/ans_role_config_video_drivers/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Use From Playbook](#use-from-playbook)
* [Role Options](#role-options)
* [Contributing](#contributing)

## Purpose

* Install and configure video card drivers for Intel and AMD cards.
* Optionally configure OpenGL 2D Acceleration, Video-Decode Acceleration, and
  Vulkan.

## Supported Operating Systems

* Arch Linux.

## Quick Start

### Use From Playbook

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans_role_config_video_drivers
   ```

2. From the project root directory, install/download the role:

   ```shell
   $ ansible-galaxy install --role-file requirements.yml --roles-path ./roles --force-with-deps
   ```

   * _NOTE:_ `--force-with-deps` _ensures subsequent calls download updates_

3. Include the role like any local role, from the project playbook:

   ```yaml
   # playbook.yml
   - hosts: localhost
     connection: local
     tasks:
       - name: "Configure persistent system bootup messages"
         ansible.builtin.include_role:
           name: ans_role_config_video_drivers
         vars:
           video_card_make: "Intel"
           video_card_series: "HD"
           config_opengl_2d_accel: true
           config_video_decode_accel: true
           config_vulkan: true
   ```

## Role Options

See the role `defaults` file, for overridable vars:

  * [defaults/main.yml](../defaults/main.yml)

Define these _required_ vars for the role:

  * `video_card_make`: either "Intel" or "AMD"
  * `video_card_series`:
      * For Intel, either "GMA" or "HD"
      * For AMD, either 

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans_role_config_video_drivers/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).

