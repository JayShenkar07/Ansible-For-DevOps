    
# Setting up Passwordless Authentication

## Using Public Key

```ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>```

ssh-copy-id: This is the command used to copy your public key to a remote machine.

-f: This flag forces the copying of keys, which can be useful if you have keys already set up and want to overwrite them.

"-o IdentityFile ": This option specifies the identity file (private key) to use for the connection. The -o flag passes this option to the underlying ssh command.

ubuntu@: This is the username (ubuntu) and the IP address of the remote server you want to access.

## Using Password
Go to the file ```etc/ssh/sshd_config.d/60-cloudimg-settings.conf```

Update `PasswordAuthentication yes`

Restart SSH -> `sudo systemctl restart ssh`

~~Following is a short demo of the setup: 

![Example Image](https://i.ibb.co/YQfnyFr/ppp1.png)

![Example Image](https://i.ibb.co/GQX9JT4/ppp2.png)

![Example Image](https://i.ibb.co/y6JXk0T/ppp3.png)


## Need of Passwordless Authentication
Ansible is a RedHat managed automation tool that is widely used in the industry for configuration management, provisioning, deployment and network management. 
It works on a push and agentless mechanism. 

To use the functionalities of Ansible seamlessly it has to access the managed nodes from a control node with ease. To establish a smooth connection between control node and managed nodes, passwordless authentication is a prerequisite step that has to be followed.
