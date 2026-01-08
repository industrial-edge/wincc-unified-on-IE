## Creating a device

Clicking on a created project will lead you to the following screen. On the left bar there will be available a tree with all the devices created. Click on the **Add new device** button to create a new one.

Use WinCC Unified PC Runtime version V20 Upd2 or lower from the hardware catalog

![device1](graphics/device1_TIAV20.png)

### Post-configuration checks

After adding the WinCC Unified PC Runtime device, verify and adjust the following settings to avoid using features that are not supported yet on Industrial Edge:

- **Runtime Collaboration**  
  Do *not* activate Runtime Collaboration.

  ![Runtime Collaboration disabled](graphics/runtime_collaboration.png)

- **Database Type**  
  Set to **SQLite** (Microsoft SQL is not supported).   
  
  ![Database Type: SQLite](graphics/database_type.png)

- **GMP / Audit Option**  
  Disable the Audit feature (WinCC Unified “Audit” is not supported). 

  ![GMP / Audit option disabled](graphics/gmp_audit.png)

- **Redundancy**  
  Do *not* enable Redundancy (unsupported).

  ![Redundancy disabled](graphics/redundancy.png)

- **Reporting**  
  Do *not* enable Reporting (unsupported).

  ![Reporting disabled](graphics/reporting.png)