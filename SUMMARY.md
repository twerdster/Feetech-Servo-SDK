# Feetech-Servo-SDK context

## Purpose

Python serial-servo SDK copied from Adam-Software and Feetech; this copy adds an inclusive ID-range scanner.

## Implementation evidence

The scanner defaults to IDs 1–253, 1,000,000 baud, protocol 0 and a local macOS serial path; it reports COMM_SUCCESS responses and model numbers.

Key entry points: `scsservo_sdk_example/ping.py`, `scservo_sdk/port_handler.py`, `setup.py`, `docs/upstream-usage.md`.

## Documentation state

The README explains operations, requirements, validation scope and limitations. Its pre-existing explanatory SVG is retained and labeled as a schematic rather than a runtime result. Source files and attribution are unchanged.

## Validation scope

Source/package metadata inspection plus rebuilt sdist/wheel and isolated installed-file checks; the installed long description matches README.md, SDK and license bytes are unchanged and README targets are absolute HTTPS URLs; no servo connection, timing validation or motor-motion test. The upstream Raspberry Pi single-ID record is separate from this scanner.

## Limitations

POSIX import expects an interactive terminal, range bounds are not checked, and communication success does not validate every device error flag. Examples are not installed entry points.
