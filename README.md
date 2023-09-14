![SDK](https://shields.microej.com/endpoint?url=https://repository.microej.com/packages/badges/sdk_5.6.json)
![ARCH](https://shields.microej.com/endpoint?url=https://repository.microej.com/packages/badges/arch_7.18.json)

# Overview

Low Level MicroEJ implementation for CPU load indicator.

# Usage

Add the content of src/main/c to your own BSP project.

## CPU Load

### Setup

By default, this CCO is FreeRTOS ready.
Tested on FreeRTOS V10.2.1.

#### For FreeRTOS

To enable the CPU Load KPI, you will need to:
- Enable `configUSE_IDLE_HOOK` define in FreeRTOS.
- Call the `cpuload_idle` function in FreeRTOS ilde hook function.
- Call the `cpuload_init` function in the FreeRTOS Java task, before the `microej_main` function call.
- Uncomment the `#define CPULOAD_ENABLED` in the [cpuload_conf.h file](src/main/c/inc/cpuload_conf.h).
- To print some CPU Load Debug prints, uncomment the `#define CPULOAD_DEBUG` in the [cpuload_conf.h file](src/main/c/inc/cpuload_conf.h).

#### An other RTOS

To configure this CCO for an other RTOS, you will need to:
- Implement the functions of the [cpuload_impl.h file](src/main/c/inc/cpuload_impl.h) for your RTOS.
- Call the `cpuload_idle` function in the RTOS ilde hook function.
- Call the `cpuload_init` function in the RTOS Java task, before the `microej_main` function call.
- Uncomment the `#define CPULOAD_ENABLED` in the [cpuload_conf.h file](src/main/c/inc/cpuload_conf.h).

### How to get the value

You may call the function `cpuload_get` in C to get the indicator.
To use the CPU Load KPI in Java, you may use the `get` method of the `com.is2t.debug.CPULoad` class.

# Requirements

N/A

# Validation

# Dependencies

- MicroEJ Architecture `7.x` or higher.

# Source

N/A

# Restrictions

None.


---
_Copyright 2021-2023 MicroEJ Corp. All rights reserved._
_Use of this source code is governed by a BSD-style license that can be found with this software._