# Linux Backup and Restore Project

# Objective
This project is designed to practice file backup and restoration techniques in Linux using tar, gzip, and rsync. 
- Create full and incremental backups
- Compress backup files
- Restore lost or deleted files
- Verify the integrity of restored files

# Project Structure
LinuxBackupProject/
├─ src/               # Sample files (documents, images)
├─ config/            # Configuration files
├─ docs/              # Documentation (README, command explanations)
├─ backup/            # Backup archives (full, incremental, text files)
└─ verification/      # Verification files to check restoration

# Setup Instructions

1. Open Terminal and navigate to your preferred location:

  cd ~

2. Create the main project folder and subfolders:

  mkdir -p LinuxBackupProject/{src,config,docs,backup,verification}
  cd LinuxBackupProject

3. Create sample files:
   Document file

  echo "Important project document" > src/document1.txt

   Configuration file

  echo "Server configuration settings" > config/server.conf

   Image data placeholder

  echo "Sample image data" > src/picture1.img

# Running the Project

1. Full Backup using tar + gzip:

  tar -czvf backup/project_backup_full.tar.gz src/ config/

2. Backup only text files:

  find src/ config/ -name "*.txt" -exec tar -rvf backup/text_files.tar {} \;
  gzip backup/text_files.tar

3. Incremental Backup using rsync:

  rsync -av src/ config/ backup/

4. Simulate Data Loss:

  rm -rf src/ config/

5. Restore from Full Backup:

  tar -xzvf backup/project_backup_full.tar.gz -C ./

# Testing / Verification

1. Check restored files:

  ls -la src/ > verification/restore_verification_src.txt
  ls -la config/ > verification/restore_verification_config.txt

2. Optional: Open the restored files to verify content:

  cat src/document1.txt
  cat config/server.conf

3. Check backup integrity:

  ls -la backup/

# Key Commands Explained

tar -czvf backup/project_backup_full.tar.gz src/ config/  -  
Creates a compressed full backup of src and config folders

find src/ config/ -name "*.txt" -exec tar -rvf backup/text_files.tar {} \;  -  Adds all .txt files to an archive


gzip backup/text_files.tar  -  Compresses the tar archive


rsync -av src/ config/ backup/  -  Performs incremental backup


rm -rf src/ config/  -  Simulates accidental deletion


tar -xzvf backup/project_backup_full.tar.gz -C ./  -  Restores files from backup


ls -la > verification/restore_verification.txt  -  Lists files to verify restoration

