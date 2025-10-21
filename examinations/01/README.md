# Examination 1 - Understanding SSH and public key authentication

Connect to one of the virtual lab machines through SSH, i.e.

    $ ssh -i deploy_key -l deploy webserver

Study the `.ssh` folder in the home directory of the `deploy` user:

    $ ls -ld ~/.ssh

Look at the contents of the `~/.ssh` directory:

    $ ls -la ~/.ssh/

## QUESTION A

What are the permissions of the `~/.ssh` directory?

The permissions of the ~/.ssh directory are RWX...... which means that only the user has any persmission to control that directory

Why are the permissions set in such a way?

Answer:

The permissions are set in such a way because the deploy user is the only one that needs to have control over the directory other wise it could be a security risk.

## QUESTION B

What does the file `~/.ssh/authorized_keys` contain?

Answer:

The file  contains this string ```ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIFc6ZCxIaB71l5dE2ANzMBM4hXnRQE8lmbP4JK0n0sB2 deploy key``` 

## QUESTION C

When logged into one of the VMs, how can you connect to the
other VM without a password?

Answer:

To connect to your other VM without a password you must first generate a SSH key pair using ```ssh-keygen -t rsa -b 4096```and follow the instructions then copy the public key into the other vm with ```ssh-copy-id -i ~/.ssh/id_rsa.pub vagrant@192.168.121.173```.

### Hints:

* man ssh-keygen(1)
* ssh-copy-id(1) or use a text editor

## BONUS QUESTION

Can you run a command on a remote host via SSH? How?

Answer:

It is possible to run a command on a remote host via ssh by adding the command at the end like this ```ssh webserver 'echo hello'```. What it does is connect to the server through ssh and runs the command and outputs it back on your machine.