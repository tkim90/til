# How to git clone from a repo if that repo is restricted

If you're in a VM trying to git clone a repo that requires an RSA key, follow these steps:
1. Create an SSH key in the local machine.
```
ssh-keygen -t rsa -b 2048 -C "email@example.com"
```
The -C command will add a comment to the RSA public key as a reference note.

2. Enter the private key file name (or press enter to have it set a default one for you).

Prompt:
```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_rsa):
```
In this step, it'll create a public and private RSA key. The prompt though is asking you what you want to name the PRIVATE RSA key file.
If you don't want a custom file name, just hit enter to continue (default is usually `id_rsa` for private and `id_rsa.pub` for the public key file)

3. Enter a passphrase for the SSH ke (or press enter to not use a passphrase at all).
```
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
```
This is for extra protection - anytime you invoke the SSH key, it'll ask you for the passphrase (if you set one here).

4. Enter the passphrase again (or press enter again if blank)

5. SSH Key created - you should now see two new files, the private and public key files:
```
$ ls
id_rsa id_rsa.pub
```

You'll need to use the PUBLIC key to configure in git.

Basically you need to provide git this public key so that when it tries to connect, it recognizes the local machine.

6. Copy the contents of the public RSA file.
```
cat ~/.ssh/id_rsa.pub | xclip
```
Translation: "print out the file located in <PATH> and use `xclip` to copy its contents to clipboard.
You don't need xclip for this, you can just manually select the contents and copy it.

7. Go to your git settings in the website (github or gitlab) and paste the public SSH key you just copied.


Gitlab has a good guide on this: 
https://docs.gitlab.com/ee/ssh/#common-steps-for-generating-an-ssh-key-pair
