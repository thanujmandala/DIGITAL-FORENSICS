# Use Sleuth Kit to Analyze Digital Evidence

Exp no :06 Date :

## Description

The Sleuth Kit (TSK) is a suite of command-line tools for analyzing disk images and recovering digital evidence. This guide outlines the steps to use TSK on a Windows machine for digital forensics.

## Step 1: Install Sleuth Kit

1. **Download Sleuth Kit:**

   Visit the official Sleuth Kit website or the provided Google Drive link(https://drive.google.com/drive/u/1/folders/1ilSFY7Tqn2L7AjQGhq8yJ8kixc_xT
   U-v) and download the latest Windows version.

2. **Install Sleuth Kit:**

   Run the installer and follow the instructions to install Sleuth Kit on your Windows machine.

## Step 2: Acquire the Disk Image

Before analysis, a bit-by-bit copy (disk image) of the storage device evidence is required.

1. **Create Disk Image:**

   - Use a forensic tool like FTK Imager or dd to create a bit-by-bit copy.
   - Ensure the image is in a TSK-supported format, such as .dd, .raw, .img, or .E01.

2. **Download Files (for this exercise):**

   - Download the following files from the Google Drive:
     - 4Dell Latitude CPi.E01
     - 4Dell Latitude CPi.E02

![Screenshot](images/page-02-screenshot-01.jpeg)

## Step 3: Mount the Disk Image (Optional)

Mounting the disk image simplifies the navigation and analysis of the file system.

1. **Mount the Image:**

   - Use a tool like OSFMount to mount the image as a virtual drive on your Windows system.
   - Note: This step is optional but can aid in easy file system navigation.

## Step 4: Analyze the File System

Use the Sleuth Kit command-line tools to examine the file system structure and locate evidence.

1. **Navigate to the Sleuth Kit Directory:**

   - Open the Command Prompt (cmd) and use the cd command to navigate to the directory where Sleuth Kit is installed (e.g., `C:\Program Files\SleuthKit\bin`).

2. **Identify File System Type with fsstat:**

   - Command:

     ```text
     fsstat [image file] > filesystem_info.txt
     ```

![Screenshot](images/page-03-screenshot-01.jpeg)

- List Partitions with mmls:
  - Command:

    ```text
    mmls [image file] > partitions.txt
    ```

  - Purpose: This command lists the partitions present within the image file.

2. **Analyze File System with fls:**

   - Command:

     ```text
     fls -r [image file] > file_list.txt
     ```

   - Purpose: The -r flag recursively lists files and directories in the file system, along with their metadata (inode numbers).

3. **Recover Deleted Files with icat:**

   - Command:

     ```text
     icat [image file] [inode number] > [output file]
     ```

   - Purpose: To extract a specific file, replace [inode number] with the inode found from the fls output.

![Screenshot](images/page-04-screenshot-01.jpeg)

## Step 5: Analyze Metadata

Extract file metadata to gain insight into a file's history, creation, and usage.

- View Metadata with istat:
  - Command:

    ```text
    istat [image file] [inode number] > metadata_info.txt
    ```

  - Purpose: Provides detailed information about a file, including timestamps (MAC times), size, and allocation status.

![Screenshot](images/page-04-screenshot-02.jpeg)

![Screenshot](images/page-04-screenshot-03.jpeg)

## Step 6: Timeline Analysis

Creating a timeline of file activity is vital for reconstructing events.

1. **Generate a Body File using fls:**

   - Command:

     ```text
     fls -m / -r [image file] > body.txt
     ```

   - Purpose: Generates a body file (body.txt) containing the essential metadata (MAC times, file paths) needed for timeline analysis.

![Screenshot](images/page-05-screenshot-01.jpeg)

2. **Create Timeline with mactime:**

   - Command:

     ```text
     mactime -b body.txt > timeline.txt
     ```

   - Purpose: Processes the body file to create a timeline (timeline.txt) sorted by the Modified, Accessed, and Changed (MAC) times of the files.

## Step 7: Generate a Report

Document the findings by compiling all the collected data into a comprehensive report.

1. **Compile the Data:**

   - Gather all the output files (e.g., filesystem_info.txt, partitions.txt, file_list.txt, metadata_info.txt, timeline.txt).

2. **Analyze and Document:**

   - Review the findings, highlight crucial evidence, and write a report summarizing the investigation's methodology and results.

![Screenshot](images/page-06-screenshot-01.jpeg)

## Step 8: Finalize and Store Evidence

Ensure all evidence and reports are securely managed to maintain integrity and follow the chain of custody.

1. **Archive Evidence:**

   - Use a secure, verifiable method to archive the original disk image and the analysis results.

2. **Store Securely:**

   - Store the archived data in a secure location, strictly adhering to the chain of custody procedures.

## Result

The Sleuth Kit experiment successfully analyzed the provided .E01 disk image — partitions and file system structure were identified, deleted files were recovered (using fls/icat), and detailed file metadata was extracted (fsstat/istat). A timeline was generated with mactime to reconstruct file activity, and all outputs were archived with hashes to preserve evidence integrity.
