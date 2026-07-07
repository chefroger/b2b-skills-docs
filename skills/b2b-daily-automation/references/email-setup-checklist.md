# Email Follow-Up Job — Setup Checklist

When the cron job `📧 邮件处理与跟进` (Job ID: `14c586a6a716`) reports no emails or falls back to stale conversation history, check this list.

## Quick Diagnostic

```bash
# 1. Is himalaya installed?
himalaya --version
# Expected: himalaya X.Y.Z

# 2. Is config present?
ls -la ~/.config/himalaya/config.toml
# Expected: file exists

# 3. Can it list emails?
himalaya envelope list --page-size 3
# Expected: shows 1-3 recent messages, OR a clear auth error
```

## Installation (macOS)

```bash
brew install himalaya
```

## Account Configuration

Run the interactive wizard:

```bash
himalaya account configure
```

Or edit `~/.config/himalaya/config.toml` manually.

### Gmail Setup

1. Enable 2FA in Google Account
2. Generate App Password: https://myaccount.google.com/apppasswords
3. Config values:
   - IMAP: `imap.gmail.com:993`
   - SMTP: `smtp.gmail.com:587`
   - Folder aliases: `sent = "[Gmail]/Sent Mail"` (critical for Gmail)

### iCloud Setup

1. Generate App Password: https://appleid.apple.com/manage-passwords/profile
2. Config values:
   - IMAP: `imap.mail.me.com:993`
   - SMTP: `smtp.mail.me.com:587`

## Verification

```bash
# Should show inbox messages (not an error)
himalaya envelope list --page-size 5

# Should send a test email successfully
himalaya message write \
  -H "To:[your.email]@yourdomain.com" \
  -H "Subject:Test" "Test body"
```

## Fallback Behavior

If himalaya is not configured, the email follow-up job SHOULD return `[SILENT]` instead of generating a report from conversation history. Conversation-history-based customer lists belong to the `👥 客户开发` job, not the email job.

## Common Errors

| Symptom | Cause | Fix |
|---------|-------|-----|
| `command not found: himalaya` | Not installed | `brew install himalaya` |
| `401 invalid token` | API key expired | Regenerate in `.env` |
| `authentication failed` | Wrong password | Use App Password, not account password |
| `save-to-Sent fails` | Missing folder alias | Add `folder.aliases.sent = "[Gmail]/Sent Mail"` |
| Empty inbox report | No IMAP connected | Check config.toml backend settings |
