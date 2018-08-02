[+] Secure Copy (scp) Cheatsheet
--------------------------------

[>] Copy remote file to local host:

$ scp your_username@192.168.0.10:<remote_file> /some/local/directory

[>] Copy local file to remote host:

$ scp <local_file> your_username@192.168.0.10:/some/remote/directory

[>] Copy local directory to remote directory:

scp -r <local_dir> your_username@192.168.0.10:/some/remote/directory/<remote_dir>

[>] Copy a file from one remote host to another:

scp your_username@<host1>:/some/remote/directory/foobar.txt your_username@<host2>:/some/remote/directory/

[>] Improve scp performance (use blowfish):

scp -c blowfish <local_file> your_username@192.168.0.10:/some/remote/directory