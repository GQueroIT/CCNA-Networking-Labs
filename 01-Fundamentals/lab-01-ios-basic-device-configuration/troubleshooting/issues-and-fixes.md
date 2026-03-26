# Issues and Fixes

## Issue 1: Interface Down
- Problem: The router interface was not responding.
- Cause: The interface was administratively down.
- Fix: Used the `no shutdown` command.

## Issue 2: No Connectivity
- Problem: The PC could not ping the router.
- Cause: Incorrect or missing IP configuration on the PC.
- Fix: Assigned correct IP address, subnet mask, and default gateway.

## Issue 3: Configuration Loss
- Problem: Configuration would be lost after reboot.
- Cause: Configuration was not saved.
- Fix: Used `copy running-config startup-config`.