# Analysis-of-the-Disk-Structure-using-Sleuth-Kit
## AIM:
To analyze the disk structure of a given disk image using Sleuth Kit tools in Kali Linux.

## REQUIREMENTS
- **Operating System**: Windows 10/11 or Kali Linux
- **Tools**:  
  - [The Sleuth Kit for Windows](https://sleuthkit.org/)  
  - Optional GUI: [Autopsy Forensic Browser](https://www.autopsy.com/)
- **Test Data**: Disk image file (`disk.dd`, `disk.img`, `.E01`)

## ARCHITECTURE DIAGRAM
```mermaid
flowchart TD
    A[Disk Image / Physical Disk] --> B[mmls - Partition Analysis]
    B --> C[fsstat - File System Metadata]
    C --> D[fls - File Listing]
    D --> E[icat - File Recovery]
    E --> F[Recovered Data / Metadata Report]
```
## DESIGN STEPS:
### Step 1:
- Obtain or create a disk image file (e.g., disk.dd) to analyze.
- Open the terminal in Kali Linux.

### Step 2:
Use Sleuth Kit tools like:
 - mmls → Examine the partition layout.
 - fsstat → View file system details.
 - fls → Get file listing.
 - icat → Recover files using inode numbers.
### Step 3:
Interpret the output to understand:
 - Partition table layout
 - File system metadata (block size, creation time, etc.)
 - Deleted and allocated files
 - Inode-based file recovery

## PROGRAM:
Sleuth Kit Disk Analysis Commands
### Partition Analysis
```bash
mmls disk.dd
```
### File System Metadata
```bash
fsstat -o 2048 disk.dd
```
### File Listing
```bash
fls -o 2048 disk.dd
```
### File Recovery
```bash
icat -o 2048 disk.dd 4 > recovered_file.txt
```
- Recovers the file associated with inode 4.
## SAMPLE WORKFLOW (Windows)
```bash
# Step 1: View partitions
mmls.exe C:\forensics\disk.dd

# Step 2: View file system details
fsstat.exe -o 2048 C:\forensics\disk.dd

# Step 3: List files
fls.exe -r -o 2048 C:\forensics\disk.dd

# Step 4: Recover a file
icat.exe -o 2048 C:\forensics\disk.dd 6 > C:\forensics\image.jpg
```
## OUTPUT:
Disk Structure Analysis Results

<img width="625" height="410" alt="image" src="https://github.com/user-attachments/assets/afa0aa66-9835-4b7c-9d1c-6c16a77b3cfc" />

<img width="518" height="461" alt="image" src="https://github.com/user-attachments/assets/24a7f0cf-b29d-40f0-ad01-d23b3d6796fd" />

<img width="637" height="462" alt="image" src="https://github.com/user-attachments/assets/699065d9-6ab6-489f-bfcf-a9d30fb932a6" />

<img width="637" height="458" alt="image" src="https://github.com/user-attachments/assets/df2be434-8696-4965-9b51-1cd10d6db73f" />

<img width="629" height="456" alt="image" src="https://github.com/user-attachments/assets/3c993b5e-7bf2-4817-8d14-da1e4e334e8d" />

<img width="529" height="442" alt="image" src="https://github.com/user-attachments/assets/5b1434d3-16d3-4706-a33e-8e4282509a0f" />

<img width="487" height="451" alt="image" src="https://github.com/user-attachments/assets/feea604b-ec39-4a28-a095-42dcdf6d1012" />

<img width="422" height="450" alt="image" src="https://github.com/user-attachments/assets/cd01b45e-4c45-4054-8bb9-fc9d6fd4d43b" />

<img width="423" height="217" alt="image" src="https://github.com/user-attachments/assets/4f0e44cd-6897-40fb-a323-46a0ea03f5e6" />


## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.
