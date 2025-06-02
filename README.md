# GitHub Actions Telegram Failure Notification Setup

This guide will help you integrate Telegram notifications into your GitHub Actions CI/CD pipeline. When a failure occurs during the pipeline, a message will automatically be sent to your Telegram group to alert your DevOps team.

---

## 📌 Step 1: Create a Telegram Bot

1. Open Telegram and search for `@BotFather`.
2. Type `/start` and then `/newbot`.
3. Provide a name and a unique username for your bot.
4. You’ll receive a **bot token** like: `7275426022:AAEPbI0Zq`

---

## 👥 Step 2: Get Your Telegram Chat ID

1. Open [Web Telegram](https://web.telegram.org).
2. Go to the group where the bot and DevOps team are added.
3. In the URL, find the **group ID** at the end of the link. 
  For example: `https://web.telegram.org/k/#-123456789`

4. Use this as the **Chat ID**. Keep the minus `-` sign: Chat ID: `-123456789`


> ✅ Make sure your bot is added to the group **and has permission to send messages**.

---

## 🔐 Step 3: Add Secrets to GitHub

Go to your GitHub repository → **Settings** → **Secrets and Variables** → **Actions** and add the following:

| Name                  | Value                       |
|-----------------------|-----------------------------|
| `TELEGRAM_BOT_TOKEN`  | `77275426022:AAEPbI0Zq`     |
| `TELEGRAM_CHAT_ID`    | `-123456789`                |

---

## ⚙️ Step 4: Update GitHub Actions Workflow

Inside `.github/workflows/telegram-notifications.yaml`, add the following job:


## ✅ Result

Now, whenever your pipeline fails during build-and-push or update-deployment-file jobs, your Telegram group will receive a notification like:

```less
🚨 GitHub Action FAILED
📦 Repo: your-org/your-repo
🔁 Branch: branch-name
🔧 Commit: [abcdef1](https://github.com/your-org/your-repo/commit/abcdef1)
👤 By: developer-username

```