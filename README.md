# Spartan Connect firmware site

Served by GitHub Pages at https://canfieldconnector.github.io/spartan-firmware/. Spartan Connect reads the signed firmware catalog here to decide which firmware each valve must run.

- `catalog.json` + `catalog.json.sig`: the production catalog, signed with Canfield's firmware signing key.
- `test/`: a separate test catalog, signed with a throwaway test key. Only debug builds of the app trust it.
- `<product>/<board>/<version>/`: one folder per release (the signed MCUboot image and its `release.json`).

**Never edit these files by hand.** Every change must be made with `tools/FirmwareRelease` in the spartan-stepper repository, which signs the catalog; see `docs/FIRMWARE_RELEASES.md` there. A hand-edited catalog fails its signature check and is ignored by the app. Published release folders must never change.
