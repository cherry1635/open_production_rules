
connect to the Hodaya.

you should encapsulate the way to Hodaya by fixing pwsh script.
scrip running compoments:
ssh -- connect to the Hodaya
gpg key -- the way to github repo authentication, and encryption Scenes.

prepare a sshd_config, and keep ssh server response alive.

break the bridge that communicated from host to server.

where to place host ed25519 key, and where to play server ed25519 key.
what the about the ssh connection test and debug reasons.

what about the key name?
**In Windows**
the key store in `~/.ssh/`
the key name should be indicated those points:
1. what is the usage of this key
> as encryption do not exposed at minimum principle, a key can be only use one way to identify which is better.
E.g. if I want to use a key to be a github.com ssh login key, the name will be like that:
    ed25519-github_login-240615.
    ed25519-login-linux-Hodaya.
and a key should be have a independent password, the password you can save in 1password. you can see the created time.

<h4>Generate a ssh key</h4>

What should be leave when you write a ssh-key Comment?

```
ssh-keygen -t ed25519 -C
```

<h4>While you should setting ssh automatic connection</h4>

using `ssh-add`, `ssh-agent`, that the system will find your private key and do the authentication in the shadow.



<h4>Write a ssh login process script</h4>

how to do a ssh test cmd

go to `~/.ssh/config` to    
```
   1   │ Host myhost
   2   │     Hostname fe80::ee:43a5:e3c3:ae62
   3   │     Port 22
   4   │     User cherry1635
   5   │     IdentityFile ~/.ssh/to_Andromeda_ed25519
   6   │
   7   │ Host majorbox
   8   │     Hostname 172.24.163.86
   9   │     Port 22
  10   │     User xiaolu
  11   │     IdentityFile ~/.ssh/to_majorbox_ed25519
  ```

make sure Hodaya has a static IPv6 addr, and config it to the ssh/config for the host.

<h4>How gonna Linux to config a static IPv6 addr and make dhcp and test the connection to the host</h4>


<h4>SSH key permission</h4>
Home Directory:

Should not be writable by others.
Recommended permission: 755 (drwxr-xr-x).
bash
Copy code
chmod 755 /home/username
.ssh Directory:

Should not be writable by others.
Recommended permission: 700 (drwx------).
bash
Copy code
chmod 700 /home/username/.ssh
authorized_keys File:

Should be writable only by the owner and readable by the owner.
Recommended permission: 600 (-rw-------).
bash
Copy code
chmod 600 /home/username/.ssh/authorized_keys

<h5>You can use `sshd -t` to check if there is a sshd_config syntax error for start SSHD service failed. </h5>