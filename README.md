# Analyzing-Passwords-with-Rainbow-Tables
Password hash analysis using RainbowCrack to evaluate corporate password policy compliance via MD5/SHA1 rainbow tables.

<h1>Overview</h1>h1>
Acting as a security analyst for a corporate network, this project verifies whether captured password hashes meet the organization's password policy requirements. Using RainbowCrack, pre-computed rainbow tables were generated and used to attempt recovery of plaintext passwords from a set of captured MD5 and SHA1 hashes.

<h1>Objective</h1>
Determine whether user-selected passwords, captured as hashes in captured_hashes.txt, comply with the company's password policy:
-Minimum 8 characters
-At least one uppercase and one lowercase letter
-At least one special character from: ! " # $ % & _ ' * @
-Hashed using MD5 or SHA1

<h1> Captured hash.txt</h1>

<img width="223" height="66" alt="image" src="https://github.com/user-attachments/assets/4d1d4140-871e-48ba-b4f0-2642bf25c2d5" />


<h1>Step 1 Identify the correct RainbowCrack charset</h1>

<img width="560" height="192" alt="image" src="https://github.com/user-attachments/assets/551e28eb-5957-496c-ad4f-ff29e0fa8d73" />

In this step I reviewd the charsets against the password policy reequirements and discovered ascii-32-95 best matches.

<h1> Step 2 Generate MD5 and SHA1 rainbow tables</h1>

<img width="550" height="412" alt="image" src="https://github.com/user-attachments/assets/5fcd2706-2506-4ecc-8591-79ab81910173" />

In this step using rtgen to generate MD5 and SHA1 rainbow tables with a plaintext length range of 1-20 characters, 1,000 chains of chain length 1,000 using the ascii-32-95 charset

<h1> Step 3 using rtsort</h1>

<img width="332" height="152" alt="image" src="https://github.com/user-attachments/assets/56911022-1a16-4415-a113-23b520a1000b" />

In this step is used rtsort to sort the generated tables

<h1>Step 4 Attempted hash recovery against captured hash files</h1>

<img width="547" height="346" alt="image" src="https://github.com/user-attachments/assets/cde180cf-ae0e-4a66-a3d6-63a4d39527b6" />

In this step I used rcrack to run the hash against the rainbow tables to see the passwords in plaintext and determined that "lmnop" does not follow password policy requirements

<h1>Key Takeaway</h1>

This lab demonstrates both the practical effectiveness of rainbow table attacks against unsalted MD5/SHA1 hashes and the importance of enforcing password policy at the point of creation — rather than assuming compliance. A policy is only as strong as its enforcement; this exercise shows how easily non-compliant passwords can slip through without active validation, and how quickly weak hashing (MD5/SHA1, both fast and unsalted) exposes them to cracking.
