Encrypt
------------
sudo gpg -e ~/Desktop/file.doc

This will prompt you to type in the persons name (public key) to encrypt with.
 
Decrypt
-----------
sudo gpg -d ~/Desktop/file.doc.pgp > ~/Desktop/file.doc


Import other users' public keys by using:

sudo gpg --import <key>