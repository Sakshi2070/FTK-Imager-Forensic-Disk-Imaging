
# Forensic Disk Imaging and Evidence Integrity

A hands-on beginner digital forensics project demonstrating logical-volume acquisition, E01 forensic imaging, integrity verification, and evidence examination using FTK Imager.

> **Project type:** Simulated practice lab  
> **Case Number:** DFIR-001  
> **Evidence Number:** E001  
> **Status:** Completed

## Project Overview

This project demonstrates the fundamental workflow of acquiring and examining a simulated NTFS evidence volume.

A 2 GB dynamically expanding VHDX virtual disk was created, formatted with NTFS, and mounted as `EVIDENCE (E:)`. Sample files were added to the volume and acquired using FTK Imager into an E01 forensic image.

The acquired image was then verified and loaded back into FTK Imager for examination.

## Objectives

- Create a simulated evidence environment using a virtual disk.
- Prepare an NTFS logical volume.
- Acquire the logical volume into E01 format.
- Review acquisition verification results.
- Record MD5, SHA-1, and SHA-256 hash values.
- Examine files and directory structures in FTK Imager.
- Document the acquisition and examination process.

## Tools and Environment

| Component | Details |
|---|---|
| Operating System | Windows 11 |
| Forensic Tool | FTK Imager |
| Virtual Disk | VHDX |
| Virtual Disk Capacity | 2 GB |
| File System | NTFS |
| Partition Scheme | MBR |
| Volume | EVIDENCE (E:) |
| Image Format | E01 |
| Hash Utility | Windows `certutil` |

## Acquisition Summary

| Field | Value |
|---|---|
| Case Number | DFIR-001 |
| Evidence Number | E001 |
| Acquisition Type | Logical Drive |
| Source Volume | E: — EVIDENCE |
| Output Image | `DFIR001_E001.E01` |
| Acquisition Log | `DFIR001_E001.txt` |
| Verification Result | Match |

The acquisition was performed on the mounted logical volume. It was **not** a complete physical-disk acquisition.

## Evidence Preparation

Five sample files were created on the simulated evidence volume:

- `Documents/employee_notes.txt`
- `Documents/confidential_data.txt`
- `Documents/employee_records.csv`
- `Images/sample_image.jpg`
- `System_Logs/investigation_log.txt`

## Verification and Integrity

FTK Imager reported a successful acquisition verification match.

The MD5 and SHA-1 values were recorded from the FTK Imager acquisition log. The SHA-256 hash of the generated E01 image was calculated twice using Windows `certutil`; both calculations produced the same value.

The hash values are documented in [`Documentation/Hash_Record.txt`](Documentation/Hash_Record.txt).

Matching SHA-256 calculations provide an integrity reference for the stored image across the two checks. They do not independently establish the authenticity of the original evidence.

## Examination

The E01 image was loaded into FTK Imager and examined.

The examination included:

- Reviewing the directory structure
- Locating the sample evidence files
- Examining text and CSV contents
- Locating the JPEG image
- Inspecting file data using Hex Viewer

## Key Learning Outcomes

- Understood the difference between a virtual disk, a mounted logical volume, and a forensic image.
- Practised logical-volume acquisition using FTK Imager.
- Learned to review acquisition verification results.
- Calculated and recorded cryptographic hashes.
- Examined evidence from an acquired E01 image.
- Documented the scope and limitations of a forensic acquisition.

## Project Documentation

- [Acquisition Report](Documentation/Acquisition_Report.md)
- [Evidence Inventory](Documentation/Evidence_Inventory.txt)
- [Hash Record](Documentation/Hash_Record.txt)
- [Screenshots](Screenshots/)

## Scope and Limitations

This was a simulated beginner lab using self-created sample evidence. It did not involve a real seized computer, physical disk acquisition, a hardware write blocker, deleted-file recovery, unallocated-space analysis, memory acquisition, or malware analysis.

The project demonstrates logical-volume acquisition and basic forensic examination. It does not claim that all physical disk structures or unallocated areas were captured.

## Conclusion

This project provided hands-on experience with forensic imaging, evidence integrity verification, cryptographic hashing, and basic forensic examination using FTK Imager.

The exercise strengthened my understanding of evidence preservation and the importance of documenting acquisition scope, verification results, and examination findings.
