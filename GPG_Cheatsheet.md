<!DOCTYPE html>
<html>
<head>
    <title>GPG Cheatsheet 🛡️</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        h1, h2, h3 {
            color: #333;
        }
        code {
            background-color: #f0f0f0;
            padding: 10px;
            border-radius: 4px;
            display: block;
        }
        pre {
            background-color: #f8f8f8;
            padding: 10px;
            border-radius: 4px;
        }
    </style>
</head>
<body>

<h1>GPG Cheatsheet 🛡️</h1>

<h2>🔑 Key Management</h2>

<p><strong>Generate a new GPG key pair:</strong></p>
<code>gpg --full-generate-key</code>

<p><strong>List all keys in your GPG keyring:</strong></p>
<code>gpg --list-keys</code>

<p><strong>List all the secret keys in your GPG keyring:</strong></p>
<code>gpg --list-secret-keys</code>

<h2>🔒 Message Encryption and Decryption</h2>

<p><strong>Encrypt a message:</strong></p>
<code>gpg -e -u "your-email@example.com" -r "recipient@example.com" message.txt</code>

<p><strong>Decrypt a message:</strong></p>
<code>gpg -o decrypted-message.txt -d message.txt.gpg</code>

<h2>📁 GPG Folder Encryption Cheat Sheet</h2>

<h3>Encrypting a Folder</h3>

<ol>
    <li><strong>Create a tarball from the folder you want to encrypt:</strong></li>
    <code>tar -czvf archive.tar.gz /path/to/folder_to_encrypt</code>

    <li><strong>Encrypt the tarball using GPG:</strong></li>
    <code>gpg -e -r your-email@example.com archive.tar.gz</code>
</ol>

<h3>Decrypting a Folder</h3>

<ol>
    <li><strong>Decrypt the GPG file to a tarball:</strong></li>
    <code>gpg -o archive.tar.gz -d archive.tar.gz.gpg</code>

    <li><strong>Extract the tarball to the original folder:</strong></li>
    <code>tar -xzvf archive.tar.gz</code>
</ol>

<h2>✉️ Encrypting a Message for Yourself: [Different Method]</h2>

<ol>
    <li><strong>Generate a Key Pair:</strong></li>
    <code>gpg --gen-key</code>

    <li><strong>Encrypt the Message:</strong></li>
    <code>gpg -e -u "Your Name" -r "Your Name" message.txt</code>

    <li><strong>Decrypt the Message:</strong></li>
    <code>gpg -d message.txt.gpg</code>
</ol>

<h2>👥 Encrypting a Message for Someone Else:</h2>

<ol>
    <li><strong>Import Their Public Key:</strong></li>
    <code>gpg --import theirkey.gpg</code>

    <li><strong>Encrypt the Message:</strong></li>
    <code>gpg -e -u "Your Name" -r "Their Name" message.txt</code>
</ol>

<h2>🔄 Exporting & Importing Keys</h2>

<p><strong>Exporting Your Public Key:</strong></p>

<ol>
    <li><strong>List your keys to find the one you want to export:</strong></li>
    <code>gpg --list-keys</code>

    <li><strong>Export it to a file:</strong></li>
    <code>gpg --export -a "Your Name" > public.key</code>
</ol>

</body>
</html>
