# LLM Garous

<img src="https://upload.wikimedia.org/wikipedia/fr/thumb/2/2c/Loups-garous_de_Thiercelieux.png/500px-Loups-garous_de_Thiercelieux.png" width="200"/>

Codebase for our project at [ISC](https://isc.hevs.ch/) to play a game of "Loups-Garous" with LLMs.

## Setup

Install dependencies:
```bash
pip install -r requirements.txt
```

Implement your `WerewolfPlayer` in `werewolf.py`.

## How to play a game

1. **Define your players** in [`players_config.json`](players_config.json). Each player has a `name`, `is_female`, and an `api_base_url` (either a local URL like `http://localhost:5021/` or a remote one like `https://my-werewolf.vercel.app/`).
2. **If you have local players, start them** with:
   ```bash
   python local_players.py
   ```
   This reads `players_config.json` and spawns one Flask server per unique localhost port. Remote players are skipped (they are expected to already be running).
3. **Start the Game Leader** with:
   ```bash
   python game_leader.py
   ```
   The leader connects to every player listed in `players_config.json` and orchestrates the game.

Add `-w` to `game_leader.py` to open the web log viewer (served by `game_webapp.py`).

# Instructions

[projet_loups_garous.pdf](projet_loups_garous.pdf)

# Deploying a player to Vercel

You can host one of your players remotely on Vercel for testing across machines or to compete against other groups.

1. Sign up at https://vercel.com/signup, choose "personal projects", continue with GitHub.
2. From the Vercel dashboard, **Import Git Repository** and select your fork of this project.
3. Vercel auto-detects `app.py` as a Flask app. Keep the defaults and click **Deploy**.
4. Once deployed, copy the project URL (e.g. `https://my-werewolf.vercel.app/`) and paste it into `players_config.json` as the `api_base_url` for that player.

Each Vercel deployment hosts a single player server. To run several remote players, deploy several Vercel projects (or use multiple branches).

# Players from last year (Vercel)

> TODO: list of public Vercel URLs of last year's players, so you can measure your players against them.
