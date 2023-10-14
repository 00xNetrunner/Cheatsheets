
```markdown
# 🔓 Hashcat Cheatsheet 🔑

Hashcat is a powerful password cracking tool. Here are some useful commands and examples:

## Table of Contents

- [Check GPUs](#check-gpus)
- [Hash Types](#hash-types)
- [Attack Modes](#attack-modes)
- [Wordlists](#wordlists)
- [Incremental Mode](#incremental-mode)
- [Custom Charsets](#custom-charsets)
- [Examples](#examples)

---

## 🕵️‍♂️ Check GPUs

- `hashcat -I` 🖥️  
  **Note**: Check available GPUs on the system.

---

## 🗝️ Hash Types

- `hashcat -m 0` 🔐  
  **Note**: MD5.
- `hashcat -m 1000` 🔑  
  **Note**: NTLM.
- `hashcat -m 2500` 🔓  
  **Note**: WPA/WPA2.
- `hashcat -m 22000` 🔓  
  **Note**: WPA-PMKID-PBKDF2.

---

## ⚔️ Attack Modes

- `hashcat -a 0` 🗡️  
  **Note**: Straight attack.
- `hashcat -a 3` 🛡️  
  **Note**: Brute-force attack.

---

## 🪄 Wordlists

- `hashcat -w 4` 📘  
  **Note**: Set workload profile.

---

## 🔨 Incremental Mode

- `-increment` ♾️  
  **Note**: Enable incremental mode.
- `-increment-min 8`  
  **Note**: Set minimum password length.
- `-increment-max 12`  
  **Note**: Set maximum password length.

---

## 🎯 Custom Charsets

- `?d?l?u` 🎲  
  **Note**: Digits, lowercase, uppercase letters.
- `?s` ❇️  
  **Note**: Special characters.
- `?a` 🎯  
  **Note**: All characters (lowercase, uppercase, digits, special).

---

## 💡 Examples

### 🚀 Brute force WPA2 PMKID hash:

```bash
hashcat -m 22000 -a 3 hash.hc22000 ?d?d?d?d?d?d?d?d
```

- `m 22000`: WPA-PMKID-PBKDF2 hash.
- `a 3`: Brute-force attack.
- `?d?d?d?d?d?d?d?d`: 8-digit brute-force mask.

### ⚡ Incremental attack on WPA2 hash:

```bash
hashcat -m 22000 hash.hc22000 --increment --increment-min 8 --increment-max 12 ?d?d?d?d?d?d?d?d?d
```

- `-increment`: Incremental mode.
- `-increment-min 8`: Min length 8.
- `-increment-max 12`: Max length 12.
- `?d?d?d?d?d?d?d?d?d`: 8-12 digit incremental mask.
```

You can copy this Markdown content into an `.md` file and upload it to your GitHub repository. This should make it easier to refer to your Hashcat commands.
