## Step 1 - Generate new SSH key pair 

```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
    
## Step 2 -  Add SSH key to SSH agent

```
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/<ssh-key-file-name>  # Only if given a passphrase!
```

## Step 3 - Copy the SSH public key

```
cat ~/.ssh/<ssh-key-file-name>.pub
```

## Step 4 - Add the SSH key to GitHub

1. Go to GitHub SSH Keys Settings.
2. Click New SSH Key.
3. Give it a title (e.g., "My Laptop").
4. Paste your public key into the "Key" field.
5. Click Add SSH Key.

## Step 5 - Add new key to `.ssh/config`

```
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/<ssh-key-file-name>
```

## Step 6 - Test the connection

```
ssh -T git@github.com
```
