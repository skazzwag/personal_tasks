## Step 1 - Generate new SSH key pair 

```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
    
## Step 2 -  Add the public key to GitHub as a signing key

1. Go to GitHub SSH and GPG Keys Settings.
2. Click "New SSH Key" (for signing, not authentication).
3. Paste your public key (~/.ssh/<new_ssh_key>.pub).


## Step 3 - Configure git to use SSH for comit signing

```
git config --global commit.gpgsign true
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
```
