
# SSH (Secure Shell)

SSH, also known as **Secure Shell** or **Secure Socket Shell**, is a network protocol that provides users, particularly system administrators, with a secure way to access a computer over an unsecured network. It also refers to the suite of utilities that implement the SSH protocol.

SSH provides strong authentication and encrypted data communications between two computers connecting over an open network such as the internet. It is widely used by network administrators for managing systems and applications remotely, allowing them to:

- Log into another computer over a network  
- Execute commands remotely  
- Move files between systems  

---

## Key Features

- Secure remote access to SSH-enabled network systems or devices  
- Secure and interactive file transfer sessions  
- Automated and secured file transfers  
- Secure issuance of commands on remote devices or systems  
- Secure management of network infrastructure components  

---

## SSH Basics

- **Default Port:** `22`  
- **Configuration file:** `/etc/ssh/sshd_config`  
- **Required Packages:** `openssh-server`, `openssh-client`, `openssh`  
- **Daemon Service:** `sshd`  

---

## SSH Authentication Types

There are two types of SSH authentication:

1. **Password Based Authentication**  
2. **Key Based Authentication**  

---

### 1. Password Based Authentication

This is the simplest method of authenticating an SSH connection to another machine. The user provides the password for the account at the time of connection.

**Syntax:**
```bash
ssh user@server_ip
````

**Example:**

```bash
[root@server0 ~]# ssh root@172.31.19.233
root@172.31.19.233's password:
```

To enable/disable password-based authentication, edit `/etc/ssh/sshd_config`:

```bash
PasswordAuthentication yes   # enable
PasswordAuthentication no    # disable
```

---

### 2. Key Based Authentication

SSH key pairs consist of a **public key** and a **private key**.

* **Private key:** Kept secret by the client.
* **Public key:** Shared with the server and stored in `~/.ssh/authorized_keys`.

If the client can prove it has the private key, the server grants access without requiring a password.

#### Steps:

1. **Generate key pair:**

   ```bash
   ssh-keygen
   ```

2. **View keys:**

   ```bash
   ls ~/.ssh/
   # authorized_keys id_rsa id_rsa.pub
   ```

3. **Add public key to authorized\_keys:**

   ```bash
   cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/id_rsa
   chmod 600 ~/.ssh/authorized_keys
   ```

4. **Transfer private key to client:**

   ```bash
   scp ~/.ssh/id_rsa root@172.25.0.10:/root
   ```

5. **Login using private key:**

   ```bash
   ssh -i /root/id_rsa root@172.25.0.11
   ```

---

## Additional SSH Examples

### Execute Single Remote Command

```bash
ssh -i /root/id_rsa root@172.25.0.11 "mkdir /dir_name2"
```

### Run Graphical Applications (X11 Forwarding)

```bash
ssh -X root@172.25.0.11
firefox &
```

### Use Custom Port

1. Edit `/etc/ssh/sshd_config`:

   ```bash
   Port 2020
   ```

2. Allow new port in SELinux:

   ```bash
   semanage port -a -t ssh_port_t -p tcp 2020
   ```

3. Restart SSH service:

   ```bash
   systemctl restart sshd
   ```

4. Open port in firewall:

   ```bash
   firewall-cmd --add-port=2020/tcp
   ```

5. Connect using custom port:

   ```bash
   ssh root@172.25.0.11 -p 2020
   ```

---


