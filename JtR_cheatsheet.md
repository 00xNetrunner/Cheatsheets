# John the Ripper Cheatsheet

John the Ripper, often called "John," is an open-source and highly flexible password-cracking tool. It supports multiple algorithms and is available on both Windows and Linux.

## Table of Contents

- [Dictionary Attacks](#dictionary-attacks)
- [Brute Force Attacks](#brute-force-attacks)
- [Tips & Additional Commands](#tips--additional-commands)

---

## Dictionary Attacks

### Basic Dictionary Attack

```bash
john --wordlist=dictionary.txt hashfile
```

- **wordlist**: This option specifies the dictionary file you'd like to use. 

**Example:**

```bash  
john --wordlist=passwords.txt hashes.txt
```

### With Rules

```bash
john --wordlist=dictionary.txt --rules hashfile
```

- **-rules**: This enables John's wordlist rules. You can also specify your own rules.

**Example:**

```bash
john --wordlist=words.txt --rules=best64.rule hashes.txt
```

---

## Brute Force Attacks

### Basic Brute Force

```bash
john --incremental hashfile 
```

**Example:**

```bash
john --incremental hashes.txt
```

### Specify Charset

```bash 
john --incremental=Digits hashfile
```

- Here, you can define custom charsets like `Digits`, `Alpha`, `AlphaNum`, etc. 

### Brute Force with Custom Charset

```bash
john --incremental=Custom --mask='?a?a?a?a' hashfile
```

**Example:**

```bash
john --incremental=Custom --mask='?a?a?a?a?a' hashes.txt
```

---

## Tips & Additional Commands

- **Resume Cracking**: Use `john --restore` to resume cracking.
- **Show Cracked Passwords**: Run `john --show hashfile` to display cracked passwords.
- **List Supported Formats**: Use `john --list=formats` to see all supported hash formats.
- **Performance Tuning**: Use `-fork=N` to distribute the task over multiple processes.  
- **Verbose Mode**: Add `vv` for a detailed output.
- **GPU Acceleration**: Versions like John the Ripper Pro support GPU acceleration with `-device=opencl`.
- **Manual Page**: Check `man john` for a complete list of options.

---
