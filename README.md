# Active Directory User Creation Script (PowerShell)

This project includes a PowerShell script that automates the creation of Active Directory (AD) users using data from a CSV file. It was tested in a virtualized Windows Server 2019 environment acting as a domain controller (`rohan.org`).

## Project Overview

- **Language:** PowerShell  
- **Environment:** Windows Server 2019 (Domain Controller)  
- **Purpose:** Automate AD user creation from a CSV file  
- **Domain:** `rohan.org`

## Files Included

- `create-ad-users.ps1` – PowerShell script to create users in AD  
- `users.csv` – Sample user data file with first name, last name, username, and password

## CSV Format

```csv
FirstName,LastName,Username,Password
Chris,Adams,CAdam,P@Ssw0rd123
Leila,Khan,LKhan,P@ssword456
```

## How It Works

The script:
- Reads each row from the CSV file
- Combines first and last name into the user's full name
- Creates a SAMAccountName and UPN using the `Username` field
- Assigns a password and places the user in the default "Users" container
- Enables each user account

The AD Path used in the script is:  
`CN=Users,DC=rohan,DC=org`

## Usage Instructions

1. Place both `create-ad-users.ps1` and `users.csv` on the domain controller (e.g., `C:\Scripts`).
2. Open PowerShell **as Administrator**.
3. Import the AD module if needed:
   ```powershell
   Import-Module ActiveDirectory
   ```
4. Run the script:
   ```powershell
   .\create-ad-users.ps1
   ```

## Example Output

```powershell
Created user: CAdam
Created user: LKhan
```

## Notes

- Modify the `-Path` value in the script if you are using a specific Organizational Unit (OU)  
- Script assumes the Active Directory PowerShell module is installed  
- Requires administrative privileges on the domain controller

## Author

**Rohan Bangash**  
GitHub: [github.com/Rohan-Bangash](https://github.com/Rohan-Bangash)




