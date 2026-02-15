
# oracle_pdb_ass_II_29085_fabrice

##  Task Explanations

### Task 1: Create a New Pluggable Database
I successfully created a persistent Pluggable Database following the required naming convention.
* **Command Used:** `CREATE PLUGGABLE DATABASE...`
* **Action:** Created the PDB `fa_pdb_29085`, opened it using `ALTER PLUGGABLE DATABASE... OPEN`, and saved its state so it remains open after a restart.
**User Creat  ion:** I switched the session container to the new PDB and created the required user `Fabrice_plsqlauca_29085` with `CONNECT`, `RESOURCE`, and `DBA` privileges

### Task 2: Create and Delete a PDB (Lifecycle Management)
To demonstrate lifecycle management, I created a temporary PDB and then removed it.
* **Creation:** Created `fa_to_delete_pdb_29085`.
* **Verification:** Opened the PDB to confirm it was active.
* [cite_start]**Deletion:** Closed the PDB using `CLOSE IMMEDIATE` and completely removed it using the `DROP PLUGGABLE DATABASE ... INCLUDING DATAFILES` command[cite: 66, 68, 72].

### Task 3: Oracle Enterprise Manager (OEM)
I accessed the Oracle Enterprise Manager Database Express dashboard to visualize the database environment.
* **Access:** Logged in via `https://localhost:5500/em`.
* [cite_start]**Verification:** Verified that `fa_pdb_29085` is listed as a mounted and open PDB in the container hierarchy[cite: 78, 82].


## Challenges Faced & Solutions
During the execution of this assignment, I encountered the following technical challenges and solved them as described:

1.  **Issue: `ORA-12541: TNS:no listener`**
    * **Description:** When trying to connect via SQL Developer, the connection failed because the listener was not responding.
    * **Solution:** I opened the Windows Services management console (`services.msc`) and manually started the `OracleOraDB21Home1TNSListener` service. I verified the status using `lsnrctl status` in the command prompt.
https://docs.oracle.com/en/database/oracle/oracle-database/21/multi/introduction-to-the-multitenant-architecture.html
2.  **Issue: `ORA-01031: insufficient privileges`**
    * **Description:** I attempted to run `ALTER PLUGGABLE DATABASE` commands while logged in as a standard `SYSTEM` user, which was denied.
    * **Solution:** I switched to the command line and logged in using `sqlplus / as sysdba`. This granted me the Super User privileges required to open, close, and drop pluggable databases.



## Screenshots
Evidence of all tasks can be found in the `screenshots/` folder of this repository:
* `task1_pdb_creation.png`: Shows the creation and open status of `fa_pdb_29085`.
* `task1_user_creation.png`: Shows the creation of user `Fabrice_plsqlauca_29085`.
* `task2_pdb_deletion.png`: Shows the creation and subsequent dropping of `fa_to_delete_pdb_29085`.
* `task3_oem_dashboard.png`: Screenshot of the OEM dashboard.



## Official Technical References

