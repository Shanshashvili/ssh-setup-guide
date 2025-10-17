---
## Description: How to connect from VS Code (SSH Remote) to a Linux VM using only username and password.

🧠 GOAL:
Connect to a Linux VM from VS Code Remote SSH extension without SSH key — only using username@PublicIP + password.

------------------------------------------------------------
⚙️ STEP 1 — Make Sure Password Login is Enabled
------------------------------------------------------------
This must be done inside the target VM (the one you want to connect to).

1. Connect using the Azure portal console or any available method.
2. Open the SSH configuration file:
       `sudo vim /etc/ssh/sshd_config`
3. Find and set the following:
   ```ssh
       PasswordAuthentication yes
       ChallengeResponseAuthentication no
   ```
5. Save the file and restart SSH:
       `sudo systemctl restart ssh`

------------------------------------------------------------
⚙️ STEP 2 — Configure VS Code SSH
------------------------------------------------------------
1. On your local machine, open or create this file:
      `~/.ssh/config`

2. Add a new host configuration:
   ```ssh
       Host myvm
         HostName <Public_IP>
         User <username>
         Port 22
   ```

   🟢 Do NOT add "IdentityFile" since we are not using keys.

4. Save the file.

------------------------------------------------------------
⚙️ STEP 3 — Connect from VS Code
------------------------------------------------------------
1. Open VS Code.
2. Install the "Remote - SSH" extension if not already installed.
3. Open the Command Palette `Ctrl+Shift+P` → "Remote-SSH: Connect to Host..."
4. Choose "myvm" (the one you added in config).
5. When prompted, enter your password.

💥 You are now connected to your VM using password authentication!

------------------------------------------------------------
⚠️ SECURITY TIPS
------------------------------------------------------------
- Make sure your password is strong.
- In Azure NSG (Network Security Group), limit inbound SSH access:
  ```ssh
      Source IP: your_public_ip
      Destination Port: 22
      Protocol: TCP
      Action: Allow
  ```
- If possible, disable password authentication later for higher security:
   ```ssh
      PasswordAuthentication no
   ```

------------------------------------------------------------
✅ SUMMARY
------------------------------------------------------------

```
✔ No SSH key required.
✔ VS Code connects through SSH Remote extension.
✔ You just need:
    → Public IP of the VM
    → Username
    → Password
```
