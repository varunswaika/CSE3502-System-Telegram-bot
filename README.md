# System Monitoring Telegram Bot

> **Archived.** No longer maintained. This repository is kept as a record and is read-only.

A Python Telegram bot that reports the host machine's uptime, CPU, memory, disk and network details on command, and logs each reply to a local MongoDB database.

## Why it is interesting

- It turns `psutil` into a small remote monitoring tool: each command handler collects one kind of system information and replies in the chat.
- Every reply is also written, with the date, to its own MongoDB collection (`uptime`, `coretemp`, `meminfo`, `diskinfo`, `ipinfo`, `cpuinfo`, `info`) in a database called `isaa`, so the bot doubles as a simple audit log.
- `/startlog` repeats the CPU, disk, network, memory and uptime reports every 60 seconds. It runs in a blocking loop, so the bot handles nothing else while it is active.

Commands:

```
/info      About the bot
/uptime    System uptime
/coretemp  CPU core temperatures (Linux only, needs the coretemp sensor)
/mem       Memory and swap usage
/disk      Usage of each mounted partition
/ip        Network interfaces, IP and MAC addresses
/cpu       Core counts, frequencies and per-core usage
/startlog  Send the reports above every 60 seconds
```

## Run it

Needs Python 3, a Telegram bot token from BotFather, and MongoDB running on `localhost:27017`.

```bash
pip install pyTelegramBotAPI psutil pymongo
export TELEGRAM_BOT_TOKEN=your-token-here
python bot.py
```

`pyTelegramBotAPI` is the package that provides the `telebot` module; `pip install telebot` installs an unrelated package.

## Tech

Python 3, pyTelegramBotAPI, psutil, pymongo, MongoDB.

## Context

VIT coursework, CSE3502 Information Security Management, Winter semester 2022.

## License

MIT, see LICENSE.
