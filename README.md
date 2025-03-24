# Daily Commit Automation

This repository automates daily commits to keep your GitHub contribution graph active. The workflow leverages **GitHub Actions** to schedule automated commits at the same time each day.

## 🚀 Features

✅ Automated daily commits at 8:30 AM IST every day.  
✅ Dynamic **commit number** tracking with proper ordinal suffixes (1st, 2nd, 3rd, etc.).  
✅ Includes current date in commit messages.  
✅ Simple, clean message format in `commit_info.md`.  
✅ Uses **PowerShell** for improved Windows compatibility.  
✅ Manual trigger supported via **workflow_dispatch**.

## 📂 Repository Structure

```
/
├── .github/
│   └── workflows/
│       └── daily_commit.yml
├── commit_info.md
├── .gitignore
├── README.md
```

## ⚙️ Setup Instructions

1. **Fork this repository** (or clone it into your own GitHub account).
2. Navigate to the repository and create the following path:
   - `.github/workflows/daily_commit.yml`
3. Copy the contents from `daily_commit.yml` into this newly created file.
4. The workflow will automatically create `commit_info.md` on its first run.
5. Go to your repository's **Settings** → **Actions** → Enable workflows (if required).
6. Manually run the workflow by going to the **Actions** tab and selecting **Run Workflow**.

## 🕒 Commit Schedule

- **Daily at 8:30 AM IST** (3:00 AM UTC)

## 📋 `commit_info.md` Example Output

```
Hi, this is my 5th commit on 2025-03-24.
```

## 🚨 Important Notes

- Ensure the email and username in the `.yml` file match your GitHub account for accurate commit tracking.
- The workflow may fail if you disable repository actions or revoke GitHub's access permissions.
- The commit message automatically includes the proper ordinal suffix for the commit number (1st, 2nd, 3rd, 4th, etc.).
- The repository requires the "Contents: Write" permission to be enabled for GitHub Actions.

## 🔧 Customization

To modify the commit schedule:
- Edit the cron expression in `daily_commit.yml`
- The format is: `minute hour * * *` (in UTC time)
- For example, `0 3 * * *` represents 3:00 AM UTC (8:30 AM IST)

To change the commit message format:
- Modify the PowerShell script in the "Update or Create Commit Info File" step
- You can customize the date format by changing the `Get-Date -Format` parameter

## 📊 How It Works

Each time the workflow runs:
1. It reads the current commit number from `commit_info.md`
2. Increments the number and determines the correct ordinal suffix
3. Gets the current date in YYYY-MM-DD format
4. Replaces the entire file content with a new message including the updated number and current date
5. Commits and pushes the changes to the repository

The workflow maintains a clean, single-line message that always displays the latest commit information.
