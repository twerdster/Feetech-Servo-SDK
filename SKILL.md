# Feetech-Servo-SDK maintenance workflow

Read `SUMMARY.md`, this file and `README.md` before editing.

## Working on the repository

Install this checkout in an isolated Python environment to exercise its SDK, not an assumed equivalent PyPI release. setup.py embeds README.md in long_description: rebuild wheel/sdist and compare installed metadata after documentation changes. Use absolute primary source and image URLs in README.md because installed long descriptions do not have a GitHub base URL. Retain upstream packager and vendor attribution.

## Documentation checks

- Check claims against the named source files and recorded results. Separate source inspection,
  configuration generation, runtime execution and benchmark evidence.
- Keep README setup requirements available without following an advanced guide. Check Markdown
  headings, links and image references, including source files omitted by a sparse checkout.
- Inspect labels inside diagrams as well as captions. Never turn a schematic or generated input
  into an implied successful run.
- Keep original source, credits and license notices intact for documentation-only changes.
- Review and synchronize `SUMMARY.md` and `SKILL.md` before every commit. Record any unrun checks
  as limitations rather than implying that validation passed.

## Current evidence boundary

Source/package metadata inspection, final wheel/sdist rebuild and isolated installation with exact README metadata, SDK and license checks; no servo connection, timing validation or motor-motion test. The upstream Raspberry Pi single-ID record is separate from this scanner.

POSIX import expects an interactive terminal, range bounds are not checked, and communication success does not validate every device error flag. Examples are not installed entry points.
