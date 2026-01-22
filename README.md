# linux-recon-toolkit
My Linux enumeration and training scripts as part of my cybersecurity learning journey.
# Linux Recon Toolkit

## Day 1 Progress (Phone Session)
- Started Linux fundamentals journey.
- Learned basic commands: ls, pwd, cd, cat.
- Studied what SSH is and why it is used in security.
- Practising Bandit levels 0-1

## Purpose
This repository will store my Linux-based recon and enumeration scripts as I build my cybersecurity skillset.

Day 1 (Practical):
- Connected to OverTheWire Bandit using SSH.
- Executed basic Linux commands: ls, pwd, whoami, cat.
- Retrieved Level 1 password from remote system.
  
### Day 1: First SSH access and Bandit Level 0 complete
🧠 Why This Was a Big Deal (Even If It Felt Simple)

Demonstrated:

Remote system access

Command-line navigation

Credential discovery

Session control

That is the foundation of both hacking and defense.

### Day 2:
- Completed Bandit Level 1 → 2.
- Learned how to handle files with special names using ./ and --.
- Practiced ls -la and safe file reading.

Day 2: Handled special filenames and completed Bandit Level 1

### Day 3:
- Completed Bandit Level 2 → 3.
- Learned Linux file permissions (rwx).
- Practiced handling filenames with spaces using quoting and escaping.
- Learned how users and groups control access to files.
Day 3: Permissions & filenames with spaces (Bandit 2→3)

### Day 4 – Hidden Files & Directory Analysis (Bandit Level 3 → 4)

- Logged into Bandit as `bandit3`.
- Identified `inhere` as a normal visible directory using `ls -la`.
- Entered the directory and used `ls -la` to discover a hidden file: `...Hiding-From-You`.
- Used path-prefixing and quoting (`cat "./...Hiding-From-You"`) to safely read the file.
- Retrieved the Level 4 password.
- Learned:
  - the difference between directories and hidden files,
  - why hidden files only show with `ls -la`,
  - how attackers hide payloads using dot-prefix filenames.
pgsql ### Day 4: Hidden file discovery and Level 3→4 password retrieval

### Day 5 – Searching with grep (Bandit Level 4 → 5)

- Logged into Bandit as `bandit4` and explored the `inhere` directory.
- Encountered multiple files named with leading dashes: `-file00` … `-file09`.
- Learned that `grep "pattern" *` failed with `grep: ile00: No such file or directory` because filenames starting with `-` were treated as options.
- Fixed this by using:
  - `grep -I "" -- *` or
  - `grep -I "" ./*`
- Identified the only file containing readable text and retrieved the Level 5 password using `cat ./-file0X`.
- Reinforced concepts:
  - wildcard expansion (`*`),
  - safe handling of filenames that look like flags,
  - and how `grep` is used in real-world log analysis and threat hunting.
 

### Day 6 – File discovery with find (Bandit Level 5 → 6)

- Explored a directory containing multiple nested subdirectories (`maybehere00`–`maybehere19`).
- Used metadata-based searching to locate a file without knowing its name.
- Applied the `find` command with filters for:
  - regular files (`-type f`)
  - exact file size (`-size 1033c`)
- Identified the correct file and retrieved the Level 6 password using `cat`.

**Key skills:** using `find`, filtering by file size and type, navigating nested directories.  
**Cyber relevance:** techniques used in forensic analysis and threat hunting to locate hidden or suspicious files.

### Day 7 – File discovery, permissions, and troubleshooting (Bandit Level 6 → 7)

- Practiced locating files based on metadata (owner, group, size) using `find`.
- Used permission-aware searching with error suppression:
  `find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null`
- Retrieved the Level 7 password by identifying and reading the correct file.
- Gained hands-on experience with Linux permission boundaries and access control.
- Debugged multiple issues including:
  - incorrect assumptions about challenge objectives,
  - missing files in expected directories,
  - permission-restricted paths,
  - and SSH environment differences on Windows (admin vs normal PowerShell).

**Key skills:** file enumeration, Linux permissions, structured troubleshooting, environment awareness.  
**Cyber relevance:** foundational skills for forensics, incident response, and threat hunting.


 ### Day 8 – Base64 decoding (Bandit Level 7 → 8)

- Identified Base64-encoded data inside `data.txt`.
- Used `base64 -d` to decode the file contents.
- Extracted the Level 8 password from the decoded output.
- Learned the difference between encoding and encryption.

**Key skills:** Base64 decoding, data inspection, malware-analysis fundamentals.

### Day 9 – Sorting and uniqueness analysis (Bandit Level 8 → 9)

- Processed a large dataset containing many duplicate lines.
- Used `sort` and `uniq -u` to identify the only unique entry.
- Retrieved the Level 9 password from the unique line.
- Practiced command chaining and anomaly detection techniques.

**Key skills:** sort, uniq, pipes, data analysis fundamentals.
 
### Day 10 – Strings and binary file analysis (Bandit Level 9 → 10)

- Inspected a binary file using `file` to determine its type.
- Used `strings` to extract readable content from binary data.
- Filtered extracted strings with `grep` to identify the password.
- Retrieved the Level 10 password.

**Key skills:** binary inspection, strings extraction, command chaining, malware-analysis fundamentals.


### Day 11 – ROT13 text transformation (Bandit Level 10 → 11)

- Identified ROT13-obfuscated text in `data.txt`.
- Used `tr` to translate alphabet characters and decode the file.
- Retrieved the Level 11 password from the decoded output.
- Learned the difference between obfuscation and encryption.

**Key skills:** tr, character translation, cipher recognition.

### Day 12 – File identification & layered decompression (Bandit Level 11 → 12)

- Copied the target file to a safe workspace in `/tmp`.
- Used `file` to identify true file types (did not trust extensions).
- Unpacked multiple layers using tools like `gunzip`, `bunzip2`, and `tar -xf`.
- Repeated the identify → extract cycle until reaching ASCII text.
- Retrieved the Level 12 password from the final extracted file.

**Key skills:** file type analysis, archive handling, layered extraction, forensic workflow.

### Day 13 – Hex dump reconstruction & layered extraction (Bandit Level 12 → 13)

- Reconstructed a binary file from a hex dump using `xxd -r`.
- Identified true file types using `file` rather than trusting extensions.
- Extracted multiple nested layers (gzip, bzip2, tar) step-by-step.
- Applied a forensic workflow: identify → extract → re-identify.
- Recovered ASCII text containing the Level 13 password.

**Cybersecurity relevance:**
This mirrors real-world forensic and malware analysis workflows where attackers layer compression or obfuscation to delay analysis. Emphasizes evidence-based decision making and safe analysis practices.

**Key tools:** xxd, file, gunzip, bunzip2, tar

### Day 14 – SSH key-based authentication (Bandit Level 13 → 14)

-Located and used an SSH private key for authentication instead of a password.
-Set correct file permissions to allow secure key usage.
-Connected to the local SSH service using ssh -i privatekey bandit14@localhost.
-Successfully authenticated as the next user via key-based login.
-Retrieved the Level 14 password from the logged-in environment.

Key skills: SSH authentication, cryptographic key usage, permission management, secure remote access.







