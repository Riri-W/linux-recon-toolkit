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




