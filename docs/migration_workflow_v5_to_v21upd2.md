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

## Migration procedure

The following sections describe the recommended migration workflow step by step.

### Step 1: Create a backup in the V5.0.0 app

Open the existing **WinCC Unified Runtime for Industrial Edge V5.0.0** app on the Industrial Edge Device.

In the **WinCC Unified Web Runtime Manager**, open the configuration settings from the left-side navigation bar. In the configuration menu, scroll down until **Export and Import Data** is visible and select it.

![Open Export and Import Data settings](graphics/migration/migration_backup_1_export_import_settings.png)

In the **Export and Import Data** view, make sure that the **Export Data** tab is selected. This tab allows you to export the current app configuration as a compressed **.tar.gz** archive file for backup or migration purposes.

Click **Start Backup** to create the backup.

![Start backup from Export Data tab](graphics/migration/migration_backup_2_start_backup.png)

After clicking **Start Backup**, the export process starts. Wait until the export process has finished.

![Backup export in progress](graphics/migration/migration_backup_3_export_in_progress.png)

When the export has been completed successfully, a success message is displayed.

![Backup completed successfully](graphics/migration/migration_backup_4_backup_success.png)

After the export has completed, verify that the backup archive file is available and stored in a safe location before proceeding with the next migration steps.