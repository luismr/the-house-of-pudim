# Configuring Git with SSH for GitHub on macOS

## Introduction

Using SSH to connect to GitHub provides a secure and convenient way to authenticate without repeatedly entering your username and password. This guide will walk you through the steps to configure Git with SSH on macOS.

## Prerequisites
- macOS with Git installed
- A GitHub account
- Terminal access

## Step 1: Check for Existing SSH Keys
Before generating a new SSH key, check if you already have one:

```sh
ls -al ~/.ssh
```

If you see files like `id_rsa.pub` or `id_ed25519.pub`, you may already have an SSH key configured.

## Step 2: Generate a New SSH Key (If Needed)
If you don't have an existing SSH key or want to create a new one, generate it using:

```sh
ssh-keygen -t ed25519 -C "your_email@example.com"
```

If your system does not support `ed25519`, use:

```sh
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

- You will be prompted to enter a file location. Press **Enter** to accept the default (`~/.ssh/id_ed25519` or `~/.ssh/id_rsa`).
- Optionally, set a passphrase for added security.

## Step 3: Add the SSH Key to the SSH Agent
Start the SSH agent and add your key:

```sh
eval "$(ssh-agent -s)"
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```

For older systems, use:

```sh
ssh-add ~/.ssh/id_ed25519
```

To ensure automatic loading on macOS, add the following to `~/.ssh/config`:

```sh
echo "Host *\n  AddKeysToAgent yes\n  UseKeychain yes\n  IdentityFile ~/.ssh/id_ed25519" >> ~/.ssh/config
```

## Step 4: Add the SSH Key to GitHub
Copy the public key to your clipboard:

```sh
pbcopy < ~/.ssh/id_ed25519.pub
```

If using `id_rsa`, replace the filename accordingly.

1. Go to [GitHub SSH Keys Settings](https://github.com/settings/keys)
2. Click **New SSH Key**
3. Paste the key into the **Key** field
4. Give it a descriptive title and click **Add SSH key**

## Step 5: Test the SSH Connection
Verify the SSH connection to GitHub:

```sh
ssh -T git@github.com
```

If successful, you should see:

```sh
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

## Step 6: Configure Git to Use SSH
Ensure Git uses SSH instead of HTTPS:

```sh
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

To change an existing repository to SSH:

```sh
git remote set-url origin git@github.com:username/repository.git
```

## Conclusion
Your macOS system is now configured to connect to GitHub using SSH. You can securely clone, push, and pull repositories without entering your credentials each time.

