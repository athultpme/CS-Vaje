# Verifying Software Integrity (SHA256 & GPG)-Exercise Report

## Prepared By

**Students Name:** Athul Thuvattu Parambath
**Enrollment Number:** 35250310

## 1. Inspect the script

![install.sh](1.png)

Q **What does this script do ?**

- It simulates a software installation by 
  - Creating a src directory
  - Creating a run.sh script that prints Hello.
  - Moving run.sh into src.
  - Executing src/run.sh

## 2. Generate SHA256 Cheksum

![Sha256](2.png)


## 3. Verified file Integrity

![File Integrity](3.png)


## 4. Gernerated GPG key Pair

![gpg](4.png)

## 5. Signed the Checksum File

![signed the checksum file](5.png)


![signed the checksum file](7.png)

## 6. Verified the Signature

![verified the signature](8.png)

## 7. Simulated a Tampering Attack

![simulation](9.png)

## Questions & Answers

### 1. Why should you never execute scripts without inspection ?

Scripts can contain malicious code that runs with your permissions. They can :

- Delete or encrypt files(ransomware).
- steal passwords, keys, or personal data.
- Install backdoors or malware.
- Modify system configuration
- Connect to attacker-controlled servers.


### 2. What does SHA256 guarantee ?

SHA256 gurantees integrity: it ensures the file has not been changed.

If even one byte is modified, the checksum will be completely different. However, SHA256 does not tell you who created the file or if it's from a trusted source.

### 3. What does GPG guarantee ?

GPG guarantees authenticity and non-repudiation:
- The file (or checksum) was signed by someone possessing the private key.
- you can verify the signer's identity via their key fingerprint.
- The signed data hasn't altered since signing.
GPG proves origin, not just integrity.

### 4. Can SHA256 prove the author of a file ?

No. SHA256 is jus a hash. anyone can compute it, and it doesn't contain any identity information.
An attacker can modify a file, compute a new SHA256, and publish both. Without a digital signature, you cannot verify who created the original file.

### 5. Why is signing the checksum important ?

Signing the checksum (not just the file) creates a two-layer trust model:
1. SHA256 verifies the file hasn't changed.
2. GPG signature verifies the checksum itself is authentic and came from the trusted author.

This prevents an attacker from replacing both the file and the checksum with their own. the signature ties the checksum to the author's identity.

### 6. What happened after the script was modified ?

After adding echo MALICIOUS CODE EXECUTED:

- The SHA256 checksum no longer matched.
- sha256sum -c returned FAILED.
- The tampering was detected before execution.

This demonstrates how checksum protect against accidental corruption and intentional tampering.

## Bonus Task

### 1. Import Kali signing key

![signing](10.png)

### 2. Download checksum signature and verify signature

![checksum](11.png)

### 3. Download Kali ISO

![kali](12.png)

- Size:4.40 GB, downloaded in ~24 minutes

### 4. Verify checksum 

![verify](13.png)

- Output: kali-linux-2026.1-installer-amd64.iso: OK
- Both check Passed, The ISo is authentic and untampered.