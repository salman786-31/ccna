# 🔐 Cisco Packet Tracer – Basic Device Security Configuration

## 📌 Project Overview

This Cisco Packet Tracer lab demonstrates the implementation of **basic security configurations** on Cisco routers and switches. The objective is to understand how to secure privileged access by configuring `enable password`, `enable secret`, and password encryption.

This project is suitable for beginners preparing for the **Cisco CCNA (200-301)** certification.

---

## 🎯 Learning Objectives

- Configure device hostnames
- Set an `enable password`
- Verify privileged EXEC authentication
- Encrypt plaintext passwords using `service password-encryption`
- Configure a secure `enable secret`
- Compare `enable password` and `enable secret`
- View encrypted passwords in the running configuration
- Save configurations to NVRAM

---

## 🖥️ Network Topology

```
           +----------------+
           |      PC1       |
           +----------------+
                  |
                  |
        +-------------------+
        |    Switch (SW1)   |
        +-------------------+
          |       |       |
          |       |       |
       +------+ +------+ +------+
       | PC2  | | PC3  | | R1   |
       +------+ +------+ +------+
```

---

## 🛠️ Configuration Steps

### Step 1 – Configure Hostnames

#### Router

```bash
enable
configure terminal
hostname R1
```

#### Switch

```bash
enable
configure terminal
hostname SW1
```

---

### Step 2 – Configure an Enable Password

```bash
enable
configure terminal
enable password CCNA
```

---

### Step 3 – Test the Password

```bash
disable
enable
```

When prompted, enter:

```
Password: CCNA
```

---

### Step 4 – Verify the Running Configuration

```bash
show running-config
```

Output example:

```text
enable password CCNA
```

The password is stored in plaintext.

---

### Step 5 – Encrypt Passwords

```bash
configure terminal
service password-encryption
```

This encrypts existing and future passwords configured with commands such as:

- `enable password`
- `line console`
- `line vty`

---

### Step 6 – Verify Encryption

```bash
show running-config
```

Example:

```text
enable password 7 0822455D0A16
```

The password is now encrypted using **Type 7 encryption**.

---

### Step 7 – Configure a Secure Enable Secret

```bash
configure terminal
enable secret Cisco
```

---

### Step 8 – Test Privileged EXEC Access

```bash
disable
enable
```

Use the following password:

```
Cisco
```

> **Note:** When both `enable password` and `enable secret` are configured, Cisco IOS always uses the `enable secret` for authentication because it is more secure.

---

### Step 9 – Verify Both Passwords

```bash
show running-config
```

Example:

```text
enable password 7 0822455D0A16
enable secret 5 $1$mERr$QdQ2...
```

| Configuration | Encryption Type |
|--------------|-----------------|
| `enable password` | Type 7 (Weak) |
| `enable secret` | Type 5 (MD5 Hash) |

---

### Step 10 – Save the Configuration

```bash
copy running-config startup-config
```

or

```bash
write memory
```

---

## 📚 Important Commands Summary

| Command | Purpose |
|----------|---------|
| `hostname R1` | Change device hostname |
| `enable password CCNA` | Configure privileged EXEC password |
| `service password-encryption` | Encrypt plaintext passwords |
| `enable secret Cisco` | Configure secure privileged password |
| `show running-config` | Display current configuration |
| `copy running-config startup-config` | Save configuration permanently |

---

## 🔒 Security Notes

- `enable password` uses **Type 7 encryption**, which is reversible and not considered secure.
- `enable secret` uses a hashed value (commonly **Type 5 MD5** on many IOS versions) and takes precedence over `enable password`.
- In production environments, always prefer `enable secret` over `enable password`.

---

## 📂 File Included

- `Basic Device Security.pkt` – Cisco Packet Tracer lab demonstrating basic device security configuration.

---

## 🎓 CCNA Topics Covered

- Basic Device Configuration
- Hostname Configuration
- Privileged EXEC Mode Security
- Enable Password
- Enable Secret
- Service Password Encryption
- Running Configuration Verification
- Configuration Management

---

## 👨‍💻 Author

**Danush Kalyan**

This project was created as part of CCNA practice to strengthen foundational Cisco networking and device security skills.