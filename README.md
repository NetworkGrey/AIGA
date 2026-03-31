[README.md](https://github.com/user-attachments/files/26385140/README.md)
# AIGA Discord Bot

Age of Empires Mobile AI Advisor  
Built by Network Grey | Powered by OpenAI

---

## Files

| File | Purpose |
|---|---|
| `bot.py` | Main bot code |
| `requirements.txt` | Python dependencies |
| `Procfile` | Railway deployment config |

---

## What This Bot Does

AIGA listens in one specific Discord channel and replies to players with Age of Empires Mobile advice using OpenAI.

Current version includes:
- single-channel operation
- per-user hourly rate limiting
- short in-memory conversation context
- Railway-friendly deployment

---

## Environment Variables

Set these in Railway under **Variables**:

| Variable | Value |
|---|---|
| `DISCORD_TOKEN` | Your Discord bot token |
| `OPENAI_API_KEY` | Your OpenAI API key |
| `AIGA_CHANNEL_ID` | `1488469269875265648` |
| `OPENAI_MODEL` | `gpt-4.1` |

### Notes
- Never hardcode tokens in the code files
- Never commit secrets to GitHub
- `AIGA_CHANNEL_ID` must be the numeric Discord channel ID, not the channel name

---

## Deployment on Railway

### Step 1 — GitHub
1. Create or open your GitHub repository
2. Upload these files:
   - `bot.py`
   - `requirements.txt`
   - `Procfile`
   - `README.md`

### Step 2 — Railway
1. Go to Railway and sign in with GitHub
2. Click **New Project**
3. Choose **Deploy from GitHub repo**
4. Select your repository

Railway should detect the `Procfile` automatically.

### Step 3 — Variables
In Railway, open your project and add:

- `DISCORD_TOKEN`
- `OPENAI_API_KEY`
- `AIGA_CHANNEL_ID`
- `OPENAI_MODEL`

### Step 4 — Deploy
Deploy the service.

If successful, Railway logs should show something like:

```txt
AIGA is online as AIGA#XXXX
Listening in channel ID: 1488469269875265648
```

---

## How It Works

- AIGA ignores all bot messages
- AIGA only replies in the configured Discord channel
- Each user gets a simple hourly quota
- A short conversation history is stored in memory for context
- If Railway restarts, that short-term memory resets

---

## Current Limitations

This version is intentionally simple.

It does **not yet** include:
- slash commands
- persistent database storage
- document retrieval / RAG
- admin dashboard
- multi-channel or multi-server configuration

---

## Recommended Next Improvements

1. Add slash commands such as `/ask` and `/help`
2. Move rate limits and memory into Postgres or Redis
3. Add retrieval over AIGA reference docs
4. Add admin logging and user feedback controls

---

## Troubleshooting

### Bot does not reply
Check:
- the bot is invited to the server
- the bot can see the channel
- the bot has permission to read and send messages
- `AIGA_CHANNEL_ID` is correct
- `DISCORD_TOKEN` is valid

### Railway deploy fails
Check:
- `requirements.txt` is present
- `Procfile` is present
- variables are set
- logs for Python import errors

### OpenAI errors
Check:
- `OPENAI_API_KEY` is valid
- the project has API access enabled
- the chosen model is available to your account

---

## Security Notes

- Keep all secrets in Railway variables
- Do not paste tokens into GitHub
- Do not paste tokens into Discord
- Rotate tokens immediately if you accidentally expose them
