# HACS Submission Guide

This guide covers the complete end-to-end process for preparing, validating, and submitting your integration to the official HACS repository.

## Phase 1: Repository Readiness
Before validation, ensure your file structure and core files are correct.

- [x] **LICENSE File**: A valid license file (e.g., Apache 2.0, MIT) must exist in the root.
  - *Current Status*: Present (`LICENSE`).
- [x] **README.md**: Must exist and describe the integration.
  - *Current Status*: Present (`README.md`).
- [x] **hacs.json**: Configuration file for HACS logic.
  - *Current Status*: Present (`hacs.json`).
- [x] **manifest.json**: Must contain valid JSON, including `version`, `issue_tracker`, and `documentation`.
  - *Current Status*: Valid in `custom_components/unavailable_devices_report/manifest.json`.

---

## Phase 2: HACS Validation (Manual Actions)
The GitHub Action `.github/workflows/validate.yaml` performs automated checks. Some failures require manual changes in GitHub settings.

### 1. Repository Metadata
**Error:** `The repository has no description` / `The repository has no valid topics`
- **Action:** Go to your GitHub Repository **Settings** (or "About" section on the main page).
- **Description:** Add a short description (e.g., "Unavailable Devices Report for Home Assistant").
- **Topics:** Add exactly these tags: `hacs`, `home-assistant`, `integration`, `python`.

### 2. Brands / Icons
**Error:** `The repository has not been added as a custom domain to the brands repo`
- **Action:**
  1. Clone [home-assistant/brands](https://github.com/home-assistant/brands).
  2. Create folder `custom_integrations/node_flow_manager`.
  3. Add your `icon.png` from `brands_assets` to that folder. (Do not add `logo.png` as the square icon is valid for both).
  4. Submit a PR to `home-assistant/brands`.

---

## Phase 3: Release & Publication

### 1. Create a GitHub Release
HACS uses GitHub Releases to serve versions to users.

1. Ensure your `manifest.json` `version` matches the tag you are about to create (e.g., `"1.0.0"`).
2. Go to your repository on GitHub -> **Releases**.
3. Click **Draft a new release**.
4. **Choose a tag**: Create a new tag (e.g., `v1.0.0`).
5. **Publish** the release.

### 2. Verify Custom Repository (Test)
Verify the integration works before submitting it globally.

1. Open Home Assistant -> HACS.
2. Click 3 locations/menu -> **Custom repositories**.
3. Add `VilniusTechnology/ha-unavailable-devices-report` as **Integration**.
4. Install and verify it loads correctly.

### 3. Submit to HACS Default Repository
To make it listed for everyone in the HACS store:

1. Go to [hacs/default](https://github.com/hacs/default).
2. Open a **New Pull Request**.
3. Follow the instructions in the PR template.
   - Typically, you will run a script or edit a lists file to append your repository URL.
4. Once merged, your integration will be public!
