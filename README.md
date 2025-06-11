# 📬 Exchange Online Shared Mailbox Auditor & Full Access Manager

This PowerShell script automates the full lifecycle of working with **Exchange Online shared mailboxes**, from exporting and auditing to granting and removing Full Access permissions. Built for admins who want one-click insights and delegation control — all in one tool.

---

## ⚙️ Features

✅ Automatically:
- 🔐 Grant Full Access permission to all shared mailboxes  
- 📄 Export shared mailbox list to CSV  
- 📊 Generate detailed activity reports (last sent/received email, permission audit) via Microsoft Graph  
- 🧹 Remove Full Access permissions afterward to maintain clean delegation  
- ⏳ Waits for permission propagation to avoid race conditions

---

## 📁 Files Generated

| File                            | Description                                      |
|---------------------------------|--------------------------------------------------|
| `SharedMailboxes_List.csv`     | List of all shared mailboxes and primary emails |
| `SharedMailboxes_Report_YYYYMMDDHHMM.csv`   | Detailed audit report using Graph API           |

All CSVs are saved to your desktop for quick access.

---

## 🧠 How It Works

1. Connects to **Exchange Online** and **Microsoft Graph API**
2. Automatically retrieves your signed-in admin UPN
3. Applies Full Access to all shared mailboxes
4. Exports data and generates reports
5. Cleans up permissions by removing Full Access from those mailboxes

---

## 🔧 Prerequisites

- PowerShell 7
- Modules:
  - `ExchangeOnlineManagement`
  - `Microsoft.Graph`

Install them using:
```powershell
Install-Module ExchangeOnlineManagement -Scope CurrentUser -Force
Install-Module Microsoft.Graph -Scope CurrentUser -Force
```
---

## 🚀 Run the Script

```powershell
.\ExchangeSharedMailboxAudit.ps1
```
✅ No need to type your UPN — the script detects it from your Exchange Online session.

---

## 🛡️ Permissions Required

Exchange Online:

Full access to run ```Get-Mailbox```, ```Add-MailboxPermission```, ```Remove-MailboxPermission```

Microsoft Graph scopes:

```Mail.Read.Shared```

Ensure your account has the appropriate rights and that Graph API consent has been granted.

---

### 📸 Sample Output

**`SharedMailboxes_Report_YYYYMMDDHHMM.csv`** includes:

| Shared Mailbox | Email Address | Subject of Last Sent | Sent Date | Sent By | Recipient | Subject of Last Received | Last Received Date | Is Last Received Read? | Full Access Users | SendAs Users |
|----------------|---------------|------------------------|-----------|---------|-----------|---------------------------|---------------------|-------------------------|-------------------|--------------|
| Finance Team   | finance@...   | Invoice Q2             | 2024-06-01 08:23 AM | Sarah | billing@... | Re: Invoice               | 2024-06-01 10:15 AM | True                    | john@...          | None         |

---

## 🧼 Cleanup
The script:

Disconnects from Graph and Exchange automatically

Cleans up permissions for audit safety

---

## 📖 License
MIT License

## ❤️ Contributions
Open an issue or PR to suggest improvements or report bugs. Let’s make Microsoft Entra reporting easy, elegant, and extensible!
