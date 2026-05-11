# Migration workflow from V5.0.0 to V21 Upd 2

This document describes the recommended workflow to migrate an existing **WinCC Unified Runtime for Industrial Edge** installation from app version **V5.0.0** to **V21 Upd 2**.

The migration is performed directly in the **WinCC Unified Runtime for Industrial Edge** app by using the backup and restore functionality.

The basic workflow is:

1. Create a backup in the existing V5.0.0 app.
2. Download and safely store the backup file.
3. Uninstall the existing V5.0.0 app.
4. Install the new V21 Upd 2 app.
5. Restore the backup in the new V21 Upd 2 app.
6. Start and validate the restored runtime project.

> **Important:**  
> Do not uninstall the existing V5.0.0 app before the backup has been successfully created, downloaded and stored in a safe location.