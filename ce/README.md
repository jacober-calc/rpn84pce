# TI-84 Plus CE Implementation

This directory contains the TI-84 Plus CE implementation of the calculator.

The code is organized in layers to keep core calculator logic independent from
hardware, OS, and toolchain details. CE-specific functionality is isolated to
the upper layers, allowing the lower layers to remain stable and reusable.

## Directory Structure

- `layer1_core/`  
  Core calculator logic.  
  This layer contains hardware-independent routines and must not depend on
  CE-specific OS calls or display code.

- `layer2_dispatch/`  
  Command dispatch and calculator state control.

- `layer3_input/`  
  TI-84 Plus CE keyboard scanning and key translation.

- `layer4_ui/`  
  User-interface state management (entry mode, cursor, display state).

- `layer5_display/`  
  Display routines for the TI-84 Plus CE.  
  The initial implementation uses monochrome output only.

- `layer6_memory/`  
  CE-specific memory layout and data storage handling.

- `layer7_system/`  
  Program entry point, OS integration, and build glue.

## Design Rules

- Lower layers must not reference CE hardware or OS routines.
- CE-specific code must remain isolated to the appropriate layer.
- Changes to core logic should not alter calculator behavior.

This structure is intentional and exists to keep the implementation modular,
maintainable, and easy to evolve.