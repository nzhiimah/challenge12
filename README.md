# Challenge 12 : Enum4linux Enumeration

#### Objective :
- To enumerate SMB information such as users, shares, NetBIOS details, and operating system information using Enum4linux.

#### Target Information :
| Item      | Value          |
|---        |---             |
| Target IP | 192.168.83.129 |
| Service   | SMB            |
| Ports     | 139, 445       |

### Tool Used :
- Enum4linux

### Steps :
1. Identify Target IP Address

Command: (Run inside Metasploitable 2)
```
ip a
```
Result :
<img width="650" height="238" alt="Screenshot 2026-05-10 151320" src="https://github.com/user-attachments/assets/816bedd8-58d3-4b63-b90c-7b9265a424bd" />
<br>

Explanation :
- The target machine IP address was identified as:
```
192.168.83.129
```
---
2. Verify SMB Ports

Command :
```
nmap -p 139,445 192.168.83.129
```
Result :
<img width="644" height="257" alt="Screenshot 2026-05-10 151709" src="https://github.com/user-attachments/assets/25b7cd5a-83a6-4b3b-a2fb-47f1f8a73d9b" />
<br>

---
3. Run Enum4linux

Command :
```
enum4linux -a 192.168.83.129
```
<img width="650" height="353" alt="Screenshot 2026-05-10 151736" src="https://github.com/user-attachments/assets/659d6e54-45e0-409a-a0f3-8fb46c5793be" />
<img width="650" height="420" alt="Screenshot 2026-05-10 151814" src="https://github.com/user-attachments/assets/c90d6d31-1423-4360-8583-d9c14e3d1308" />
<br>
Findings :

- NetBIOS Information

| Information | Details |
|---|---|
| Computer Name | METASPLOITABLE |
| Workgroup | WORKGROUP |
<br>

<img width="650" height="134" alt="Screenshot 2026-05-10 151833" src="https://github.com/user-attachments/assets/c66b5ba7-1f66-4516-8a8f-2096272599ae" />
<br>
Findings :

- OS Information

| Information | Details |
|---|---|
| Operating System | Unix/Linux |
| SMB Software | Samba 3.0.20 |
<br>

<img width="282" height="460" alt="Screenshot 2026-05-10 151859" src="https://github.com/user-attachments/assets/4a1736cb-a4bc-4c19-9108-396a48e2d95f" />
<br>
Findings :

- User Enumeration

| Username |
|---|
| games |
| nobody |
| msfadmin |
| root |
| user |
<br>

<img width="650" height="442" alt="Screenshot 2026-05-10 151919" src="https://github.com/user-attachments/assets/37c8acda-2d3f-4df7-9cb5-0eaba0cb7de7" />

<br>
Findings:

- SMB Shares

| Share Name |
|---         |
|print$      |
| tmp |
| opt |
| IPC$ |
| ADMIN$ |

---
### Conclusion
- Enum4linux successfully gathered detailed SMB-related information from the target machine.
