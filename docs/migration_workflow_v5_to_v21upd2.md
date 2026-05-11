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

In the WinCC Unified Web Runtime Manager, open the configuration settings from the left-side navigation bar.

![Open configuration settings](graphics/migration_backup_1_open_settings.png)

In the configuration menu, scroll down and select **Export and Import Data**.

![Select Export and Import Data](graphics/migration_backup_2_export_import_menu.png)

The **Export Data** page is used to create a backup of the current app configuration.  
This export is created as a compressed **.tar.gz** archive file and can be used for backup or migration purposes.

![Export Data page](graphics/migration_backup_3_export_data_page.png)

Click **Start Backup** to begin the export process.

![Start backup](graphics/migration_backup_4_start_backup.png)

Wait until the export process has finished successfully. A success message is shown after the backup has been completed.

![Backup completed successfully](graphics/migration_backup_5_backup_success.png)

Before continuing with the migration, make sure that the backup was created successfully.