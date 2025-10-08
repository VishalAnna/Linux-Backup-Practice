Linux Backup and Restore Project
--------------------------------

Project Overview:
-----------------
The objective of this project is to practice file backup and restoration techniques on Linux using 
tar, gzip, and rsync. This includes creating full backups, text-file-specific backups, incremental 
backups, restoring lost files, and verifying the integrity of restored files.

Project Structure:
-----------------
LinuxBackupProject/
├─ src/                # Sample files (documents, images)
├─ config/             # Configuration files
├─ backup/             # Backup archives (full, incremental, text files)
├─ docs/               # Documentation (README, commands explanation, final report)
└─ verification/       # Verification files to check restoration

Key Commands Used:
-----------------
1. Full Backup:
   tar -czvf backup/project_backup_full.tar.gz src/ config/
   - Creates a compressed archive of all source and configuration files.

2. Text File Backup:
   find src/ config/ -name "*.txt" -exec tar -rvf backup/text_files.tar {} \;
   gzip backup/text_files.tar
   - Backs up only .txt files and compresses the archive.

3. Incremental Backup:
   rsync -av src/ config/ backup/
   - Copies only changed files to backup folder.

4. Simulate Data Loss:
   rm -rf src/ config/
   - Deletes sample files to simulate accidental loss.

5. Restore from Backup:
   tar -xzvf backup/project_backup_full.tar.gz -C ./
   - Restores all files from the full backup archive.

6. Verify Restoration:
   ls -la src/ > verification/restore_verification_src.txt
   ls -la config/ > verification/restore_verification_config.txt
   - Ensures all files are restored correctly.

Verification:
-------------
- All original files are restored successfully from the backups.
- Verification text files contain the directory listing of restored files.
- Backups were tested to confirm integrity and proper restoration.

Challenges Faced:


Real-World Applications:
------------------------
- Linux system administrators regularly use backup and restore techniques to prevent data loss.
- Automating backups with tar, gzip, and rsync is useful for project versioning, server configuration, and disaster recovery.

GitHub Repository:
------------------


Submission Notes:
-----------------
- Project folder includes all source files, configuration files, backup archives, documentation, 
  and verification outputs.
- README file contains setup, run, and test instructions.
- This final report summarizes the project workflow, commands, verification, and challenges.
