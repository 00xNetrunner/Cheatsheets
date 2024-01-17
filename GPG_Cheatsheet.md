# GPG Cheatsheet 🔐

## Key Management 🔑

- **Generate a new GPG key pair:**

```bash
gpg --full-generate-key
```

- **List all keys in your GPG keyring:** 

```bash
gpg --list-keys
```

- **List all the secret keys in your GPG keyring:**

```bash
gpg --list-secret-keys
```

## Message Encryption and Decryption 💌

- **Encrypt a message:**

```bash
gpg -e -u "your-email@example.com" -r "recipient@example.com" message.txt
```

This creates `message.txt.gpg`.

- **Decrypt a message:**

```bash
gpg -o decrypted-message.txt -d message.txt.gpg
```

This creates `decrypted-message.txt`.

## GPG Folder Encryption Cheat Sheet 📂

### Encrypting a Folder 🔒

1. **Create a tarball from the folder you want to encrypt:**

```bash
tar -czvf archive.tar.gz /path/to/folder_to_encrypt
```

2. **Encrypt the tarball using GPG:** 

```bash
gpg -e -r your-email@example.com archive.tar.gz
```

### Decrypting a Folder 🔓

1. **Decrypt the GPG file to a tarball:**

```bash  
gpg -o archive.tar.gz -d archive.tar.gz.gpg
```

2. **Extract the tarball to the original folder:**

```bash
tar -xzvf archive.tar.gz
```

## Encrypting a message for yourself: [Different Method] 🤔

1. **Generate a Key Pair**:

```bash 
gpg --gen-key
```

2. **Encrypt the Message**:

```bash
gpg -e -u "Your Name" -r "Your Name" message.txt
```

3. **Decrypt the Message**: 

```bash
gpg -d message.txt.gpg
```

## Encrypting a message for someone else: 🤝 

1. **Import Their Public Key**:

```bash
gpg --import theirkey.gpg
```

2. **Encrypt the Message**:

```bash 
gpg -e -u "Your Name" -r "Their Name" message.txt
```

## Exporting & Importing Keys 📤📥

1. **Exporting Your Public Key:**

```bash
gpg --list-keys
gpg --export -a "Your Name" > public.key
```

