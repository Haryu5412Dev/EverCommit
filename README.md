# EverCommit

Simple tool to keep your GitHub contribution graph active. Automatically makes commits on a schedule using GitHub Actions.

## Setup

### 1. Fork or Clone This Repository

Click the "Fork" button at the top right, or clone this repo:

```bash
git clone https://github.com/YOUR_USERNAME/EverCommit.git
cd EverCommit
```

### 2. Create a GitHub Personal Access Token (PAT)

1. Go to GitHub Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Click "Generate new token (classic)"
3. Give it a descriptive name (e.g., "EverCommit Token")
4. Select the following scopes:
   - `repo` (Full control of private repositories)
   - `workflow` (Update GitHub Action workflows)
5. Click "Generate token"
6. **IMPORTANT:** Copy the token immediately - you won't see it again!

### 3. Add the Token to Repository Secrets

1. Go to your forked repository
2. Click Settings → Secrets and variables → Actions
3. Click "New repository secret"
4. Name: `PAT_TOKEN`
5. Value: Paste your personal access token
6. Click "Add secret"

### 4. Configure Your Settings

Edit the `config.yml` file to customize your preferences:

```yaml
# Your GitHub username (will be used for commits)
github_username: "YOUR_GITHUB_USERNAME"

# Your email (use your GitHub noreply email for privacy)
github_email: "YOUR_EMAIL@users.noreply.github.com"

# Commit frequency (min and max commits per day)
min_commits: 1
max_commits: 5

# Schedule (cron format - default is 8 AM UTC daily)
# Format: 'minute hour day month weekday'
# Examples:
#   '0 8 * * *'   - Every day at 8 AM UTC
#   '0 */6 * * *' - Every 6 hours
#   '0 0 * * 1'   - Every Monday at midnight
schedule_cron: '0 8 * * *'

# Commit message format (use {timestamp} placeholder)
commit_message: "Activity update - {timestamp}"

# File to update with activity logs
activity_file: "ACTIVITY.md"
```

### 5. Enable GitHub Actions

1. Go to the "Actions" tab in your repository
2. If prompted, click "I understand my workflows, go ahead and enable them"
3. The workflow will now run automatically based on your schedule

### 6. Done

That's it. The workflow runs automatically. You can also manually trigger it from the Actions tab if needed.

## Customization

Edit `config.yml` to change settings:
- `min_commits` / `max_commits` - How many commits per run
- `schedule_cron` - When to run (default: daily at 8 AM UTC)
  - `0 8 * * *` = Daily at 8 AM
  - `0 */6 * * *` = Every 6 hours
  - `0 9 * * 1-5` = Weekdays at 9 AM
- `commit_message` - Customize the commit message

**Tip:** Use GitHub's noreply email for privacy: `USERNAME@users.noreply.github.com`

## Troubleshooting

**Not working?**
- Check Actions tab is enabled
- Verify PAT_TOKEN secret is set correctly
- Make sure your PAT has `repo` and `workflow` scopes

**Important:** Never commit your PAT token - always use GitHub Secrets

## License

MIT License
