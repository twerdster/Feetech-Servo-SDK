# Feetech-Servo-SDK

[![Python](https://img.shields.io/badge/code-Python-3776AB?logo=python&logoColor=white)](https://github.com/twerdster/Feetech-Servo-SDK/tree/main/scservo_sdk)
[![Serial bus](https://img.shields.io/badge/interface-pyserial-555555)](https://github.com/twerdster/Feetech-Servo-SDK/blob/main/scservo_sdk/port_handler.py)
[![License: Unlicense](https://img.shields.io/badge/license-Unlicense-green)](https://github.com/twerdster/Feetech-Servo-SDK/blob/main/LICENSE)

This repository contains a Python interface to Feetech serial servos and example programs for
pinging devices, reading and writing registers, and issuing synchronized operations. It copies
[Adam-Software/Feetech-Servo-SDK](https://github.com/Adam-Software/Feetech-Servo-SDK), which packaged
code from [Feetech's SCServoSDK](https://gitee.com/ftservo/SCServoSDK).

![Schematic of Python, a serial adapter and a shared servo bus](https://raw.githubusercontent.com/twerdster/Feetech-Servo-SDK/main/docs/images/servo-bus-scan.svg)

*Schematic of the SDK and ID scanner. It does not identify attached hardware or record a successful scan.*

## Behavior in this copy

[scsservo_sdk_example/ping.py](https://github.com/twerdster/Feetech-Servo-SDK/blob/main/scsservo_sdk_example/ping.py) accepts a serial device, baud rate,
protocol and inclusive ID range. It sends a ping to each ID and prints the IDs and model numbers
whose communication result is `COMM_SUCCESS`. The defaults are IDs 1–253, 1,000,000 baud and a
machine-specific macOS device path. `--protocol 0` selects STS/SMS byte ordering; `1` selects SCS.

The library is in [scservo_sdk/](https://github.com/twerdster/Feetech-Servo-SDK/tree/main/scservo_sdk/). The examples
`scsservo_sdk_example/read_write.py`, `scsservo_sdk_example/sync_write.py` and
`scsservo_sdk_example/sync_read_write.py` write goal position and speed registers
and can move motors. Inspect their register values before execution; `ping.py` only sends ping
requests and is the first example to use for device discovery. The original vendor archive is retained under [scsservo_sdk_source/](https://github.com/twerdster/Feetech-Servo-SDK/tree/main/scsservo_sdk_source/).

## Install and scan

Use Python 3, a serial adapter suitable for the servo bus, a powered servo and access to the
serial device. Installing from this checkout installs the SDK and its `pyserial` dependency:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install .
python scsservo_sdk_example/ping.py \
  --device /dev/ttyUSB0 --baudrate 1000000 --protocol 0 --id_start 1 --id_end 253
```

Replace the device, baud rate and protocol with values for the connected hardware. Run the example
from an interactive terminal: on POSIX systems it reads terminal attributes at import time,
even though the scanner does not use the key-reading helper. Keep the requested ID range within
the device protocol's usable addresses; the script does not validate range ordering or bounds.

The PyPI package named `feetech-servo-sdk` is a separately published distribution whose SDK
modules were not compared with this checkout. The examples in this repository are separate
source files, not installed command-line entry points.

## Validation and limitations

Review date: 2026-11-12.

The inherited README recorded a successful single-ID ping on Raspberry Pi Linux 5.15.61-v8+
(aarch64), Python 3.9.2, with model number 1540. That is an upstream example record, not a test of
this copy's range scanner. See [the preserved upstream usage record](https://github.com/twerdster/Feetech-Servo-SDK/blob/main/docs/upstream-usage.md).

This documentation revision reviewed `ping.py`, the serial-port implementation and package
metadata, rebuilt the source distribution and wheel, and checked that the installed package
metadata contains this README and the SDK files match the source. It did not connect to a servo,
test motor motion or validate timing and register behavior.
There is no automated hardware test suite in the repository. A successful communication result
alone is not a check of every device error flag or a guarantee that a servo is ready for motion.

## Attribution and license

The vendor archive referenced by the original packaging is
[SCServo_Python_200831.7z](https://gitee.com/ftservo/SCServoSDK/blob/e4d07f43c4c34827b2e226cf5cc706576504ebeb/SCServo_Python_200831.7z).
Existing source credits and [the Unlicense](https://github.com/twerdster/Feetech-Servo-SDK/blob/main/LICENSE) are retained. The vendor archive is unchanged;
its contents have not received a separate license review. Package metadata continues to
credit the upstream packager, `vertigra`; the documentation does not replace that attribution.
