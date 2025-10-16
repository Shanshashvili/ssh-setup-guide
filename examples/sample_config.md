---

# SSH Config Examples


---
## Single Server


```ssh
Host myserver
  HostName 20.120.10.45
  User azureuser
  IdentityFile ~/.ssh/mykey.pem
  Port 22  # optional
```

---

## Multiple Server

```ssh
Host dev-server
HostName 10.1.0.5
User ubuntu
IdentityFile ~/.ssh/dev-key.pem


Host staging-server
HostName 13.84.24.56
User ubuntu
IdentityFile ~/.ssh/staging-key.pem


Host prod-server
HostName 52.180.23.10
User azureuser
IdentityFile ~/.ssh/prod-key.pem
Port 2222 # example custom port
```
