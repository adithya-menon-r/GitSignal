# GitSignal

GitSignal is a low-maintenance, automated tool that uses GitHub Actions and the GitHub API to periodically check a list of repositories for newly created issues since the last recorded check. If new issues are found, it sends you an email with the issue details using an SMTP server. This tool helps eliminate manual checking and keeps you updated on new issues in repositories you want to track.

## How to Use

1. Fork this repository to your own GitHub account.

2. Get the required credentials:
   - A [GitHub Personal Access Token (PAT)](https://github.com/settings/personal-access-tokens) with Repository access set to `Public repositories`.
   - A [Google Account App Password](https://myaccount.google.com/apppasswords) for your Gmail account.

3. Add the following GitHub repository secrets in your fork:
   - `EMAIL` – Your Gmail address  
   - `PASSWORD` – Your Google App Password  
   - `TOKEN` – Your GitHub Personal Accesss Token  

4. Configure the repositories to track by editing `repos.txt`:
   ```plaintext
    owner1/repo1
    owner1/repo2
    owner2/repo2
    owner3/repo3
   ```

5. Enable the GitHub Actions schedule:
   - Open `.github/workflows/main.yml`

   - Uncomment the `on:` block:
     ```yaml
     on:
        schedule:
            - cron: '0 * * * *'
        workflow_dispatch:
     ```
     > ⚠️ **Note**: The current default schedule is to run every hour. You can change the schedule to run less frequently to save GitHub Actions minutes.

6. Commit your changes, and you are all set!

## License
[LICENSE](LICENSE)
