# 🛡️ Veeam Backup Report Automation

This repository contains two PowerShell scripts that generate Veeam backup reports from the last 7 days. The reports are exported to `.csv` files on the user's desktop.

## 📁 Scripts

### 1. `Veeam_Backup_Report_7Days.ps1`
Generates a backup status report for **all primary backup types**, including:

- VMware VM backups
- Windows/Linux agents
- SQL backups
- Backup syncs

### 2. `Agent_Backup_Report_7Days.ps1`
Filters backups based on job name patterns such as:

- `Agent`
- `Physical`
- `Laptop`
- `Workstation`

Useful for auditing **endpoint protection** and **laptop/workstation backups**.

---

## 📊 Report Fields

Each CSV report includes:

- `JobName` – Backup job name
- `BackupType` – Type of backup (e.g., VmBackup, WindowsAgent)
- `ObjectName` – Name of VM or device
- `LatestBackupTime` – Timestamp of most recent restore point
- `Repository` – Backup repository used
- `Status` – Backup health: `Success`, `Failed`, or `Warning`

---

## ⚙️ Prerequisites

Before running or scheduling the scripts:

- Veeam Backup & Replication Console must be installed.
- PowerShell module `Veeam.Backup.PowerShell` must be available.
- Execution policy should allow scripts to run:
  ```powershell
  Set-ExecutionPolicy RemoteSigned -Scope LocalMachine

