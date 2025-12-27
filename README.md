 Cracking Password Hashes with John the Ripper (Kali Linux)

 Project Overview

This project demonstrates how **password hashes can be cracked using John the Ripper on Kali Linux**. The objective is to understand **password weaknesses, cracking techniques, and security implications** from an ethical hacking and defensive security perspective.

All activities are performed in a **controlled lab environment** strictly for **educational and security auditing purposes**.

---

Objectives

* Understand password hashing and cracking concepts
* Use John the Ripper for password auditing
* Apply multiple cracking techniques
* Analyze cracked passwords to identify weaknesses
* Learn the importance of strong password policies

---

 Pre-Requisites

* Basic understanding of hashing concepts
* Familiarity with Linux command line
* Awareness of password security best practices

---

Tools & Environment

* **Operating System:** Kali Linux
* **Password Cracking Tool:** John the Ripper (Jumbo)
* **Terminal:** Bash Shell
* **Test Files:** Sample hash files and wordlists

---

 Lab Setup

```
Attacker Machine: Kali Linux
Target: Password Hash Files (Lab-generated)
```

---

Installation & Verification

John the Ripper is pre-installed on Kali Linux.

 Verify Installation

```bash
john
```

 Install (if required)

```bash
sudo apt update
sudo apt install john -y
```

---

 TASK 1: Basic Password Cracking

 Step 1: Create Hash File

```bash
echo '$1$KpixtOtB$VVujBpNkbVnv1BjlBJl6S/' > passwords.txt
```

 Step 2: Crack Password

```bash
john passwords.txt
```

 Step 3: View Results

```bash
john --show passwords.txt
```

**✔ Outcome:**
John successfully identifies weak passwords using default cracking rules.

---

TASK 2: Cracking with Custom Wordlist

 Step 1: Create Wordlist

```bash
echo -e "password\n123456\nletmein\nqwerty" > wordlist.txt
```
 Step 2: Run John with Wordlist

```bash
john --wordlist=wordlist.txt passwords.txt
```

 Step 3: Display Cracked Passwords

```bash
john --show passwords.txt
```

**✔ Outcome:**
Common passwords are cracked faster using targeted wordlists.

---

 TASK 3: Cracking Shadow File Hashes

 Performed only on authorized lab systems

 Step 1: Combine passwd and shadow

```bash
sudo unshadow /etc/passwd /etc/shadow > shadow_hashes.txt
```

 Step 2: Crack Hashes

```bash
john shadow_hashes.txt
```

 Step 3: View Results

```bash
john --show shadow_hashes.txt
```

**✔ Outcome:**
Demonstrates real-world Linux password auditing techniques.

---

 TASK 4: Incremental (Brute-Force) Mode

 Step 1: Run Incremental Mode

```bash
john --incremental passwords.txt
```

 Step 2: Stop if Required

```bash
Ctrl + C
```

**✔ Outcome:**
Highlights the risk of short and simple passwords against brute-force attacks.

---

 TASK 5: Rules-Based Password Cracking
 Step 1: Apply Default Rules

```bash
john --rules passwords.txt
```

### Step 2: Show Results

```bash
john --show passwords.txt
```

**✔ Outcome:**
Password mutation rules significantly increase cracking success rates.

---

 Security Learnings

* Weak passwords are easy to crack
* Wordlists and rules dramatically improve attack success
* Brute-force attacks are effective but time-consuming
* Strong passwords should be:

  * Long
  * Complex
  * Unique
  * Random

---
 Real-World Relevance

This project reflects real-world **SOC and VAPT activities**, including:

* Password audits
* Compliance checks
* Internal security testing
* Risk assessments

---

Ethical Considerations

All cracking activities were performed **only on authorized systems**. Unauthorized password cracking is illegal and unethical.

---

 Conclusion

This lab provided hands-on experience with **password cracking techniques using John the Ripper** and reinforced the importance of **strong password policies and secure hashing mechanisms**.

---

 Project Files

```
password-cracking-john/
│── passwords.txt
│── wordlist.txt
│── shadow_hashes.txt
│── README.md
```

---

 Future Enhancements

* Compare John the Ripper with Hashcat
* Use large real-world wordlists (e.g., rockyou)
* Explore GPU-based cracking
* Implement password policy recommendations

---

**Project Title:** Cracking Password Hashes with John the Ripper
**Domain:** Cybersecurity • Password Security
**Platform:** Kali Linux
**Author:** Sudeep
