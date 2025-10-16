# 🔹 SSH Setup Quick Guide (VSCode + Config)


1️⃣ Install SSH extension in VSCode
- Open VSCode → Extensions → search for `Remote - SSH` → Install.


2️⃣ Generate SSH key pair (if you don’t have one)
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
- Default path: ~/.ssh/id_rsa
- Public key: ~/.ssh/id_rsa.pub
- Leave passphrase empty or set one.


3️⃣ Upload public key to remote server
- Add the contents of id_rsa.pub to ~/.ssh/authorized_keys on the server.
- Set permissions:
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys


4️⃣ Create/edit SSH config file
- Path: ~/.ssh/config
- Permissions: chmod 600 ~/.ssh/config


5️⃣ Add entry for your server
Host myserver
HostName <REMOTE_IP_OR_DNS>
User <REMOTE_USERNAME>
IdentityFile ~/.ssh/id_rsa
Port 22 # optional if different from default


6️⃣ Connect via VSCode
- Press F1 → Remote-SSH: Connect to Host... → select myserver
- Or from terminal: ssh myserver


7️⃣ Optional: Multiple servers
Host dev-server
HostName 10.1.0.5
User ubuntu
IdentityFile ~/.ssh/dev-key.pem


Host prod-server
HostName 52.180.23.10
User azureuser
IdentityFile ~/.ssh/prod-key.pem


💡 Tips
- Always set correct permissions on .ssh folder & keys.
- Use meaningful Host names.
- Keep one config file for all servers.
