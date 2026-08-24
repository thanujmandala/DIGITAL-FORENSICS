**Experiment.1**

**FTK Imager: A Forensic Imaging Tool Overview**

**Acquiring Volatile Memory (RAM) Using FTK Imager**

**Link for installation file :-**
[link](https://d1kpmuwb7gvu1i.cloudfront.net/Imgr/4.7.3.81%20Release/Exterro_FTK_Imager\_%28x64%29-4.7.3.81.exe)

Steps to Capture RAM Using FTK Imager

1\. Run as Administrator

-   Open FTK Imager with administrative privileges.
-   Right-click the FTK Imager icon and select Run as administrator
-   

**2. Initiate Memory Capture**

-   In the top menu bar, click File → Capture Memory from the dropdown
    list.

    <img width="1448" height="769" alt="Screenshot (45)" src="https://github.com/user-attachments/assets/f22e7c4c-b6dc-47d4-88d9-17b2eb76023f" />


**3. Configure Destination**

A dialog box will appear where you configure where and how the memory
will be saved.

-   **Destination Path:**\
    Click **Browse** to select a folder on an **external drive** (not
    the system drive).

-   **Destination Filename:**\
    You can keep the default memdump.mem or assign a more descriptive
    name.

    <img width="1444" height="763" alt="Screenshot (46)" src="https://github.com/user-attachments/assets/a59f57f9-d4b5-48a3-a7a2-f44f1253beb6" />


-   **Optional: Include pagefile.sys**\
    Check this box to capture pagefile.sys, which is virtual memory
    stored on the disk.

-   **Optional: Create AD1 file**\
    Saves the memory dump in an AccessData-specific container file.

    <img width="1456" height="762" alt="Screenshot (47)" src="https://github.com/user-attachments/assets/78273193-c1ea-4198-8951-6e3653e38834" />


**4. Start Capture**

-   Click the **Capture Memory** button to begin acquisition.

-   <img width="1458" height="744" alt="Screenshot (48)" src="https://github.com/user-attachments/assets/4087354c-5924-465c-b429-d609e4f3ac68" />


**5. Wait for Completion**

-   A progress bar will indicate the capture status.

-   Capture time depends on the system's RAM size.

-   Once finished, the memory dump file will be available in the
    destination folder.

    <img width="1446" height="765" alt="Screenshot (49)" src="https://github.com/user-attachments/assets/1e8759a9-bd9b-4048-910d-f298b94615c3" />


**Acquiring Non-Volatile Memory (Disk Image) Using FTK Imager**

1\. Start the Process

-   In FTK Imager, go to the top menu bar: File → Create Disk Image\....

**2. Select Source Evidence Type**

A window will appear asking you to choose the source type:

-   **Physical Drive:** Images the entire disk, including all
    partitions, unallocated space, and the Master Boot Record (MBR).

-   **Logical Drive:** Images a specific partition (e.g., C: drive).

-   **Image File:** Converts or copies an existing image file.

-   **Contents of a Folder:** Creates an image of a specific folder
    only.

    <img width="1457" height="760" alt="Screenshot (50)" src="https://github.com/user-attachments/assets/26a6ce79-8be2-4086-aa60-14f84243d2c0" />


**3. Select the Source Drive**

-   From the dropdown, choose the physical drive to image (connected
    via **write-blocker**).

-   Click **Finish**.

**4. Configure the Image Destination**

-   Click **Add\...** in the \"Create Image\" window to define the
    image **format** and **destination**.

    <img width="1447" height="778" alt="Screenshot (51)" src="https://github.com/user-attachments/assets/315ae8d7-8208-4c9f-8da4-85791e5485fa" />


**Options:**

-   **Image Type:**

    -   **E01 (EnCase Format):** Recommended; includes compression,
        metadata, and error-checking.

    -   **Raw (DD):** Bit-for-bit copy with no extra features.

<img width="520" height="283" alt="Screenshot (55)" src="https://github.com/user-attachments/assets/7bed58dc-821a-4e49-b9ea-a8a5eba81e58" />

-   **Fill in Evidence Item Information:**

    -   Enter case details, examiner name, and description.

    -   This information is stored in the image metadata (important for
        documentation).

```{=html}
<!-- -->
```
-   **Choose Destination Folder:**

    -   Must be a different drive from the source.

    -   Name the image file (e.g., Case001_SuspectHDD).

-   **Image Fragment Size:**

    -   Set a value to split the image into multiple parts.

    -   Set to 0 for a single image file.

**5. Start the Imaging Process**

-   Click **Finish** to return to the \"Create Image\" screen.

-   **Check \"Verify images after they are created\"** to calculate hash
    values and ensure integrity.

-   Click **Start**.

**6. Completion and Hash Verification**

-   The imaging process may take time depending on the drive size.

-   After completion, FTK Imager verifies the hashes automatically.

-   A final window shows **MD5** and **SHA1** hashes for both the source
    drive and image.

-   Matching hashes confirm the forensic image's integrity.

-   <img width="1419" height="741" alt="Screenshot 2025-08-31 165800" src="https://github.com/user-attachments/assets/15bb6d54-4078-426b-8921-1a5324570be1" />
-   <img width="1053" height="250" alt="Screenshot 2025-08-31 174812" src="https://github.com/user-attachments/assets/a71c56b4-384c-478a-8417-0d8517c2a0c7" />



**References**

-   [FTK Imager Official
    Website](https://accessdata.com/product-download/ftk-imager-version-4-5)

-   FTK Imager Documentation
