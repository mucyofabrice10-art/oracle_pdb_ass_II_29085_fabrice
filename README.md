#  Oracle Pluggable Databases(PDB) Management Assignment
Names:Mucyo Fabrice

ID:29085

##  Task Explanations

### Task 1: Create a New Pluggable Database
I successfully created a persistent Pluggable Database following the required naming convention.
* **Command Used:** `CREATE PLUGGABLE DATABASE...`
* **Action:** Created the PDB `fa_pdb_29085`, opened it using `ALTER PLUGGABLE DATABASE... OPEN`, and saved its state so it remains open after a restart.
**User Creat  ion:** I switched the session container to the new PDB and created the required user `Fabrice_plsqlauca_29085` with `CONNECT`, `RESOURCE`, and `DBA` privileges

### Task 2: Create and Delete a PDB
To demonstrate lifecycle management, I created a temporary PDB and then removed it.
* **Creation:** Created `fa_to_delete_pdb_29085`.
* **Verification:** Opened the PDB to confirm it was active.
* **Deletion:** Closed the PDB using `CLOSE IMMEDIATE` and completely removed it using the `DROP PLUGGABLE DATABASE ... INCLUDING DATAFILES`.

### Task 3: Oracle Enterprise Manager (OEM)
I accessed the Oracle Enterprise Manager Database Express dashboard to visualize the database environment.
* **Access:** Logged in via `https://localhost:5500/em`.
**Verification:** Verified that `fa_pdb_29085` is listed as a mounted and open PDB in the container hierarchy[cite: 78, 82].


## Challenges Faced & Solutions
During the execution of this assignment, I encountered the following technical challenges and solved them as described:

1.  **Issue: `ORA-12541: TNS:no listener`**
    * **Description:** When trying to connect via SQL Developer, the connection failed because the listener was not responding.
    * **Solution:** I opened the Windows Services management console (`services.msc`) and manually started the `OracleOraDB21Home1TNSListener` service. I verified the status using `lsnrctl status` in the command prompt.

2.  **Issue: `ORA-01031: insufficient privileges`**
    * **Description:** I attempted to run `ALTER PLUGGABLE DATABASE` commands while logged in as a standard `SYSTEM` user, which was denied.
    * **Solution:** I switched to the command line and logged in using `sqlplus / as sysdba`. This granted me the Super User privileges required to open, close, and drop pluggable databases.

## Challenges Faced & Solutions
Issue: Encountered error ORA-65019 when attempting to open the PDB.

Solution: Recognized that the PDB was already in READ WRITE mode. Verified the status using the show pdbs command rather than re-running the open command.

## Integrity Statement
I certify that this assignment is my own individual work. I have not copied commands, screenshots, or code from classmates or AI tools. All evidence provided reflects my own execution of the tasks.

## Screenshots
Evidence of all tasks can be found in the `screenshots/` folder of this repository:
* `task1_pdb_creation.png`: Shows the creation and open status of `fa_pdb_29085`.
* `task1_user_creation.png`: Shows the creation of user `Fabrice_plsqlauca_29085`.
* `task2_pdb_deletion.png`: Shows the creation and subsequent dropping of `fa_to_delete_pdb_29085`.
* `task3_oem_dashboard.png`: Screenshot of the OEM dashboard.

##  Final Checklist (Apply Before Submission)

- [ ] Correct PDB names used  
- [ ] User created inside the PDB  
- [ ] Temporary PDB created and deleted  
- [ ] OEM dashboard screenshot included  
- [ ] GitHub repository is PUBLIC  
- [ ] README is clear and professional  
- [ ] Deadline respected
