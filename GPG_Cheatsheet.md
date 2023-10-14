
## GPG cheatsheet

### Key Management

- **Generate a new GPG key pair:**

\`\`\`bash
gpg --full-generate-key
\`\`\`

- **List all keys in your GPG keyring:**

\`\`\`bash
gpg --list-keys
\`\`\`

- **List all the secret keys in your GPG keyring:**

\`\`\`bash
gpg --list-secret-keys
\`\`\`

# Message Encryption and Decryption

- **Encrypt a message:**

\`\`\`bash
gpg -e -u "your-email@example.com" -r "recipient@example.com" message.txt
This creates message.txt.gpg.
\`\`\`

- **Decrypt a message:**

\`\`\`bash
gpg -o decrypted-message.txt -d message.txt.gpg
\`\`\`

- This creates `decrypted-message.txt`.

# GPG Folder Encryption Cheat Sheet

## Encrypting a Folder

1. **Create a tarball from the folder you want to encrypt:**

    Replace **`/path/to/folder_to_encrypt`** with the path to your folder and **`archive.tar.gz`** with the desired name for your tarball.

    \`\`\`bash
    tar -czvf archive.tar.gz /path/to/folder_to_encrypt
    \`\`\`

2. **Encrypt the tarball using GPG:**

    Replace **`your-email@example.com`** with your email and **`archive.tar.gz`** with your tarball's name. This will create an encrypted file named **`archive.tar.gz.gpg`**.

    \`\`\`bash
    gpg -e -r your-email@example.com archive.tar.gz
    \`\`\`

## Decrypting a Folder

1. **Decrypt the GPG file to a tarball:**

    This will decrypt the **`archive.tar.gz.gpg`** file back to **`archive.tar.gz`**.

    \`\`\`bash
    gpg -o archive.tar.gz -d archive.tar.gz.gpg
    \`\`\`

2. **Extract the tarball to the original folder:**

    This will extract the contents of the tarball to the current directory.

    \`\`\`bash
    tar -xzvf archive.tar.gz
    \`\`\`

Please note that the person performing the decryption and extraction will need the GPG private key that corresponds to the public key used to encrypt the file.

# Encrypting a message for yourself: [Different Method]

1. **Generate a Key Pair**: If you haven't already, you'll need to generate a GPG key pair. You can do this with the **`-gen-key`** option:

    \`\`\`bash
    gpg --gen-key
    \`\`\`

    Follow the prompts to set your name, email address, and passphrase.

2. **Encrypt the Message**: You can now encrypt a message with your public key. For example, to encrypt a message in a file named **`message.txt`**, you can use the following command:

    \`\`\`bash
    gpg -e -u "Your Name" -r "Your Name" message.txt
    \`\`\`

    Replace "Your Name" with the name you used when generating your key pair. This will create an encrypted file named **`message.txt.gpg`**.

3. **Decrypt the Message**: To decrypt the message, you can use the **`gpg`** command with the **`d`** option:

    \`\`\`bash
    gpg -d message.txt.gpg
    \`\`\`

    You'll be asked for the passphrase you used when generating your key pair.

# Encrypting a message for someone else:

1. **Import Their Public Key**: Before you can encrypt a message for someone else, you'll need their GPG public key. Once you have it, you can import it with the **`-import`** option:

    \`\`\`bash
    gpg --import theirkey.gpg
    \`\`\`

    Replace "theirkey.gpg" with the filename of their public key.

2. **Encrypt the Message**: You can now encrypt a message with their public key. For example, to encrypt a message in a file named **`message.txt`**, you can use the following command:

    \`\`\`bash
    gpg -e -u "Your Name" -r "Their Name" message.txt
    \`\`\`

    Replace "Your Name" with your name and "Their Name" with the name associated with their public key. This will create an encrypted file named **`message.txt.gpg`**.

The recipient will then be able to decrypt the message using their private key.

# Exporting & Importing Keys

**Exporting Your Public Key:**

1. List your keys to find the one you want to export:

    \`\`\`bash
    gpg --list-keys
    \`\`\`

2. Once you've identified the key you want to export (it's usually your email address or name), use the **`-export`** option with the **`a`** (armor) flag to export it to a file:

    \`\`\`bash
    gpg --export -a "Your Name" > public.key
    \`\`\`

    Replace "Your Name" with the name or email associated with the key you want to export. This will create a file named **`public.key`** containing your public key.
