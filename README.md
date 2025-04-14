# 🛡️ Bypass Windows Defender VBS Script

**Author**: [atulhack](https://github.com/atulhacks/atulhacks)  
**Contact**: GitHub profile linked above  
**Purpose**: Demonstrates how to disable various Windows Defender features using VBScript and PowerShell

---

## ⚠️ DISCLAIMER

> 🚨 **For Educational and Ethical Use Only**  
> This script is provided strictly for **educational**, **penetration testing**, and **authorized red team** scenarios.  
> Do **not** use this script on systems without **explicit permission**. Unauthorized use may violate local laws and regulations.

---

## 📜 Description

This VBScript leverages Windows administrative privileges to disable key Windows Defender features both through direct registry modifications and PowerShell commands. It is useful for understanding how endpoint defenses can be disabled and for developing defensive countermeasures.

---

## ⚙️ Features

- Automatically escalates privileges via UAC prompt
- Disables Windows Defender using `RegWrite`:
  - AntiSpyware engine
  - Real-Time Protection
  - IOAV Protection
  - Behavior Monitoring
- Executes the following PowerShell commands in the background:
  - `Set-MpPreference -DisableRealtimeMonitoring $true`
  - `Set-MpPreference -DisableScriptScanning $true`
  - And others...

---

## 🧪 Use Case

- ✅ Security research
- ✅ Red team labs (sandbox/VMS)
- ✅ Malware analysis training
- ✅ Understanding Windows Defender attack surfaces

> ⚠️ **Never execute this script on a production machine.**

---

## 🛡️ Defender Hardening Tips (Blue Team)

To defend against scripts like this:
- Enable **Tamper Protection** in Windows Security
- Use **AppLocker** or **Windows Defender Application Control (WDAC)** to restrict script execution
- Monitor changes to the following registry paths:
  - `HKLM\SOFTWARE\Policies\Microsoft\Windows Defender`
- Disable VBScript execution via Group Policy where applicable
- Use **Sysmon** + **SIEM** for detecting PowerShell-based attacks

---

## 🧾 How It Works

1. **Elevation Check**:
   - If not run as admin, uses `ShellExecute` with `"runas"` to relaunch elevated.
2. **Registry Edits**:
   - Uses `WScript.Shell.RegWrite` to modify Defender policies.
3. **PowerShell Execution**:
   - Calls PowerShell invisibly to apply additional `Set-MpPreference` configurations.

---

## 🧩 File Contents

```plaintext
Script.vbs  # Main VBS script
README.md            # Documentation (this file)
