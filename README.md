# WinCC Unified for Industrial Edge application example

This example shows how to use the Industrial Edge App "WinCC Unified Runtime".

- [WinCC Unified for Industrial Edge application example](#wincc-unified-for-industrial-edge-application-example)
  - [Description](#description)
    - [Overview](#overview)
    - [General Task](#general-task)
  - [Requirements](#requirements)
    - [Prerequisites](#prerequisites)
    - [Used components](#used-components)
  - [Documentation](#documentation)
  - [Contribution](#contribution)
  - [License and Legal Information](#license-and-legal-information)

## Description

### Overview

This repository provides an example of how to install, configure and use **SIMATIC WinCC Unified Runtime for Industrial Edge** and how to engineer a corresponding WinCC Unified project in TIA Portal.

WinCC Unified Runtime for Industrial Edge provides HMI functionality on an Industrial Edge Device, including visualization, alarming, logging and communication with external data sources.

![WinCC Unified Runtime for Industrial Edge](docs/graphics/introimage2.png)

### General Task

The documentation covers the basic setup and operation of **SIMATIC WinCC Unified Runtime for Industrial Edge**, as well as additional engineering, migration and diagnostic workflows.

See the [Documentation](#documentation) section for the available guides.

## Requirements

### Prerequisites

The following prerequisites are required for the basic workflows described in this repository:

- Access to an Industrial Edge Management (IEM)
- An Industrial Edge Device onboarded to the IEM
- A supported web browser
- TIA Portal for engineering WinCC Unified projects

For workflows that require communication with a PLC, the following additional components are required:

- A PLC that can be reached from the Industrial Edge Device
- A corresponding TIA Portal project containing the PLC configuration

### Used components

The following component versions were used for the workflows documented in this repository:

| Component | Version |
| --- | --- |
| SIMATIC WinCC Unified Runtime for Industrial Edge | V21 Upd 2 |
| Industrial Edge Management (IEM) | V2.4 |
| Industrial Edge Virtual Device | V1.24 or newer |
| TIA Portal | V21 Upd 1 or higher |
| S7-PLCSIM Advanced | V8.0 |

> **Note:**
> S7-PLCSIM Advanced is only required when a simulated PLC is used. A physical PLC can be used instead where applicable.

## Documentation

You can find the main documentation in the following links:

* [Installation and Tutorial](docs/installation_and_tutorial.md)
* [Further engineering workflows](docs/further_engineering_workflows.md)
* [Migration workflow from V5.0.0 to V21 Upd 2](docs/migration_workflow_v5_to_v21upd2.md)
* [Trace Settings](docs/trace_settings.md)


You can find further documentation and help in the following links:

* [Industrial Edge Hub](https://iehub.eu1.edge.siemens.cloud/#/documentation)
* [Industrial Edge Forum](https://www.siemens.com/industrial-edge-forum)
* [Industrial Edge landing page](https://new.siemens.com/global/en/products/automation/topic-areas/industrial-edge/simatic-edge.html)
* [Industrial Edge GitHub page](https://github.com/industrial-edge)

## Contribution

Thank you for your interest in contributing. Anybody is free to report bugs, unclear documentation, and other problems regarding this repository in the Issues section.
Additionally everybody is free to propose any changes to this repository using Pull Requests.

If you haven't previously signed the [Siemens Contributor License Agreement](https://cla-assistant.io/industrial-edge/) (CLA), the system will automatically prompt you to do so when you submit your Pull Request. This can be conveniently done through the CLA Assistant's online platform. Once the CLA is signed, your Pull Request will automatically be cleared and made ready for merging if all other test stages succeed.

## License and Legal Information

Please read the [Legal information](LICENSE.txt).
