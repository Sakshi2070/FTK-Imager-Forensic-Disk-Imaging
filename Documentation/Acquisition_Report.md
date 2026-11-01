
# Forensic Disk Imaging and Evidence Integrity

**Case Number:** DFIR-001  
**Evidence Number:** E001  
**Examiner:** sakshi 


---

## 1. Introduction

This project demonstrates the practical process of forensic imaging and evidence integrity verification using FTK Imager.

A simulated corporate investigation scenario was created in which a virtual evidence volume contained potentially relevant files. Before examining the evidence, a forensic image of the selected logical volume was acquired to preserve its accessible contents for examination.

The exercise was conducted in a controlled Windows 11 environment using a virtual hard disk (VHDX).

## 2. Objectives

The objectives of this exercise were:

- Understand forensic imaging and evidence preservation.
- Create a simulated evidence environment using a virtual disk.
- Acquire an evidence image in E01 format.
- Calculate and record cryptographic hashes.
- Verify the acquired forensic image.
- Examine files and directory structures using FTK Imager.
- Maintain acquisition documentation and evidence records.

## 3. Lab Environment

| Component | Configuration |
|---|---|
| Operating System | Windows 11 |
| Forensic Tool | FTK Imager |
| Evidence Storage | VHDX |
| Virtual Disk Capacity | 2 GB |
| Partition Scheme | MBR |
| File System | NTFS |
| Volume Label | EVIDENCE |
| Drive Letter | E: |
| Acquisition Format | E01 |

The virtual disk was dynamically expanding and stored at:

`C:\FTK_Forensics_Project\Source_Disk\Evidence_Disk.vhdx`

## 4. Evidence Preparation

A simulated evidence environment was created on the EVIDENCE (E:) volume.

The following files were prepared:

**Documents**
- employee_notes.txt
- confidential_data.txt
- employee_records.csv

**Images**
- sample_image.jpg

**System Logs**
- investigation_log.txt

A total of five sample files were placed on the virtual evidence volume.

These files represented simulated corporate documents, employee records, an image and system activity logs. All sample evidence was prepared specifically for this exercise.

## 5. Forensic Acquisition Methodology

FTK Imager was executed with administrative privileges.

The following acquisition procedure was performed:

1. Selected File → Create Disk Image.
2. Selected **Logical Drive** as the evidence source.
3. Selected the EVIDENCE (E:) volume.
4. Selected E01 as the output image format.
5. Entered the case and evidence identification details.
6. Configured the output directory.
7. Enabled image verification after acquisition.
8. Started the acquisition process.

**Acquisition type:** Logical Drive acquisition

**Output location:**

`C:\FTK_Forensics_Project\Output\`

**Generated image:**

`DFIR001_E001.E01`

An accompanying acquisition log was also generated.

## 6. Cryptographic Hashing and Verification

Cryptographic hashes were used to document evidence integrity.

The FTK Imager acquisition log contained the MD5 and SHA-1 values generated during the acquisition and verification process.

**Acquisition Hashes**

- **MD5:** 24b945c3cac9f4a88cdd81767136a166
- **SHA-1:** c96c3b83033784b10ab4d11911479545d6f377bf

FTK Imager reported a successful verification match.

An additional SHA-256 hash was calculated for the generated E01 image using the Windows `certutil` utility.

**Command used:**

```powershell
certutil -hashfile "C:\FTK_Forensics_Project\Output\DFIR001_E001.E01" SHA256
```

The SHA-256 calculation was repeated, and both calculations produced the same value.

**E01 Image SHA-256:** f43234895adc73985da17b47308f3df2da085b147ccc9949267ed93a2bd55ea3

The matching results confirm that the stored E01 image produced a consistent SHA-256 hash across the two checks. This provides an integrity reference for the image at those points in time.

## 7. Forensic Image Examination

The generated E01 image was loaded into FTK Imager using the Add Evidence Item option.

The following examination activities were performed:

- Explored the evidence directory structure.
- Identified the Documents, Images and System_Logs directories.
- Examined employee_notes.txt.
- Examined employee_records.csv.
- Inspected sample_image.jpg.
- Used the Hex Viewer to examine the underlying file bytes.

The expected five sample files were accessible within the acquired image.

## 8. Results and Observations

The acquisition and examination produced the following results:

| Test | Result |
|---|---|
| Virtual evidence disk creation | Successful |
| NTFS volume preparation | Successful |
| Logical Drive E01 acquisition | Successful |
| Acquisition log generation | Successful |
| FTK Imager verification | Match |
| MD5 and SHA-1 recording | Completed |
| SHA-256 repeat calculation | Match |
| E01 image loading | Successful |
| Directory examination | Successful |
| Text and CSV examination | Successful |
| Hex Viewer examination | Successful |

No acquisition verification mismatch was reported.

## 9. Scope and Limitations

This was a simulated forensic exercise, not an investigation involving an actual seized corporate computer.

The acquisition was performed using FTK Imager's **Logical Drive** option on a mounted VHDX volume.

Therefore, this exercise demonstrates logical volume acquisition and does not establish a complete physical disk acquisition. It should not be interpreted as a full physical-disk image or as proof that all unallocated disk space and disk-level structures were captured.

The exercise did not include deleted-file recovery, unallocated-space analysis, memory acquisition or malware analysis.

The sample files were created specifically for this exercise and do not represent actual corporate evidence.

## 10. Conclusion

The project successfully demonstrated the fundamental process of forensic evidence acquisition, integrity verification and examination using FTK Imager.

A simulated NTFS logical volume was acquired in E01 format, and FTK Imager reported a successful verification match.

The generated forensic image was subsequently examined, and the expected directory structure and sample files were accessible.

An additional SHA-256 fingerprint was calculated for the stored E01 image and independently recalculated to confirm consistency across both checks.

This exercise provided practical experience with logical volume acquisition, cryptographic hashing, evidence preservation and forensic documentation.

**Project Status: Completed**
