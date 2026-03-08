# 🎵 Spotify Music Analysis — Phase 1 Complete Team Plan
**Course Project | Big Data Pipeline | Hadoop + Python**
**Dataset:** Spotify Tracks Dataset (Kaggle, ~600,000 rows)
**Team Size:** 3 people | **N = 3**
**Deadline:** 1 Day

---

## 📌 QUICK NAVIGATION

| | Jump To |
|---|---|
| 🛠️ | [Team Setup — GitHub, Teams, Repo](#️-team-setup--do-this-before-anything-else) |
| **A** | [Jeevan — Repo Setup, Teams, Work Division](#section-a--jeevan-sets-up-the-repo-do-this-first-alone) |
| **B** | [Sri Lakshmi + Deepesh — Clone Repo](#section-b--sri-lakshmi-and-deepesh-clone-the-repo-each-person-does-this-on-their-own-machine) |
| **C** | [How to Push Work to GitHub](#section-c--how-to-submit-your-work-all-three-members-follow-this-every-time) |
| **D** | [File Naming Rules](#section-d--repo-file-naming-rules-everyone-must-follow-this) |
| ✅ | [Instructor Requirements Checklist](#-cross-check-with-instructor-requirements) |
| ⚡ | [Work Division at a Glance](#-work-division-at-a-glance) |
| 🕐 | [Timeline — 1 Day](#-timeline-1-day) |
| 👤 | [**Jeevan's Tasks** — Task 1 + Task 3](#-jeevans-tasks) |
| 👤 | [**Sri Lakshmi's Tasks** — Task 2 + Task 4](#-sri-lakshmis-tasks) |
| 👤 | [**Deepesh's Tasks** — Task 5 EDA](#-deepeshs-tasks) |
| 📄 | [Final Report Structure](#-final-report-structure) |
| 📌 | [Important Reminders](#-important-reminders) |

---

# 🛠️ TEAM SETUP — DO THIS BEFORE ANYTHING ELSE

> Jeevan handles all of Section A. Sri Lakshmi and Deepesh only do Section B and C on their own machines.

---

## SECTION A — JEEVAN SETS UP THE REPO (Do this first, alone)

### A1 — Prepare the GitHub Repository

Your repo is already created at:
```
https://github.com/Seimei95/Spotify_Music_Analysis.git
```

1. Go to your repo on GitHub
2. Create the following folder structure by adding a blank `.gitkeep` file inside each folder:
   ```
   Spotify_Music_Analysis/
   ├── notebooks/          ← Sri Lakshmi and Deepesh put their .ipynb files here
   ├── data/               ← DO NOT push CSVs here (too large). Just a placeholder.
   ├── screenshots/        ← All HDFS screenshots go here
   ├── reports/            ← Final compiled report goes here
   ├── logs/               ← Work Division file and Meetings Log go here
   └── README.md           ← Already exists or create it
   ```
3. In each empty folder, create a file called `.gitkeep` (no content needed) so GitHub tracks the folder

---

### A2 — Invite Teammates to GitHub

1. Go to your repo: `https://github.com/Seimei95/Spotify_Music_Analysis`
2. Click **Settings** → **Collaborators** → **Add people**
3. Add Sri Lakshmi and Deepesh by their GitHub usernames or email addresses
4. Also add your TA as a collaborator (ask your TA for their GitHub username)
5. Set all of them as **Write** access

---

### A3 — Create the Work Division File

In the `logs/` folder, create a file called `work_division.md` and paste this:

```
# Work Division — Spotify Music Analysis Phase 1

## Task Assignments

| Task | Person | Description |
|------|--------|-------------|
| Task 1 — Problem Statement | Jeevan | Write ML tasks, objectives, input/output spec |
| Task 2 — Data Sources | Sri Lakshmi | Dataset documentation and citation |
| Task 3 — HDFS Setup | Jeevan | Docker, Hadoop setup, raw + cleaned ingestion |
| Task 4 — Data Cleaning | Sri Lakshmi | 6 cleaning operations in Jupyter Notebook |
| Task 5 — EDA | Deepesh | 6 EDA operations, charts, summary |
| Final Report Assembly | Jeevan | Compile all sections into final report |

## Member Acknowledgements

I, Jeevan, acknowledge the above work division and take responsibility for my assigned tasks.
Signed: _______________

I, Sri Lakshmi, acknowledge the above work division and take responsibility for my assigned tasks.
Signed: _______________

I, Deepesh, acknowledge the above work division and take responsibility for my assigned tasks.
Signed: _______________
```

---

### A4 — Create the Meetings Log File

In the `logs/` folder, create a file called `meetings_log.md` and paste this:

```
# Meetings Log — Spotify Music Analysis Phase 1

## Meeting 1
Date: [fill in today's date]
Attendees: Jeevan, Sri Lakshmi, Deepesh
Discussion: Agreed on project topic (Spotify dataset), divided tasks, set up GitHub repo and SourceHut mailing list
Progress: All members set up their environments
Next steps: Jeevan downloads dataset and sets up HDFS. Sri Lakshmi starts cleaning. Deepesh installs dependencies.

## Meeting 2
Date: [fill in]
Attendees: [fill in]
Discussion: [fill in]
Progress: [fill in]
Next steps: [fill in]
```

> Keep updating this file after every meeting or discussion. The TA will check it.

---

### A5 — Set Up Microsoft Teams (for team communication)

Teams is free with any university or Microsoft account and is used for all team discussions, file sharing, and meeting logs.

1. Go to **https://teams.microsoft.com** and sign in with your university email (or create a free Microsoft account at microsoft.com if you don't have one)
2. Click **Teams** on the left sidebar → **Join or create a team**
3. Click **Create team** → **From scratch** → **Private**
4. Name it: `Spotify Music Analysis - Phase 1`
5. Click **Add members** and invite Sri Lakshmi and Deepesh using their university emails

---

### A6 — Set Up Channels Inside the Team

Once the team is created, add the following channels so discussions stay organized:

| Channel Name | What it's for |
|---|---|
| **General** | Default channel, use for announcements |
| **task-1-problem-statement** | Jeevan's notes and decisions |
| **task-2-data-sources** | Sri Lakshmi's updates |
| **task-3-hdfs** | Jeevan's HDFS progress and screenshots |
| **task-4-cleaning** | Sri Lakshmi's cleaning updates and errors |
| **task-5-eda** | Deepesh's EDA updates and chart previews |
| **file-handoffs** | Use this ONLY to share files between teammates |

To add a channel: Click the **...** next to your team name → **Add channel** → name it → **Standard** → Create.

---

### A7 — Rules for Using Teams

- **Every time you finish a task**, post a message in the relevant channel saying what you did (e.g., "Finished Operation 3 - duplicates removed, 4,500 rows dropped")
- **Every time you hand off a file**, post it in **#file-handoffs** with a clear message like "spotify_cleaned.csv ready for Deepesh"
- **Every meeting or discussion**, paste a short summary into **General** — this serves as your Meetings Log
- **If you hit an error**, paste the error message in the relevant channel so teammates can help

---

## SECTION B — SRI LAKSHMI AND DEEPESH: CLONE THE REPO (Each person does this on their own machine)

### B1 — Install Git
If you don't have Git installed:
- **Windows:** Download from https://git-scm.com/download/win and install
- **Mac:** Open Terminal and run `git --version` — it will prompt you to install if missing
- **Linux:** Run `sudo apt install git`

---

### B2 — Clone the Repository
Open your terminal and run:

```bash
git clone https://github.com/Seimei95/Spotify_Music_Analysis.git
cd Spotify_Music_Analysis
```

You now have the full project folder on your machine.

---

### B3 — Set Up Your Identity (one time only)
```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

---

## SECTION C — HOW TO SUBMIT YOUR WORK (All three members follow this every time)

Every time you finish a piece of work (a notebook, a screenshot, a report section), do the following:

### C1 — Put your file in the right folder
- Notebooks → `notebooks/` folder
- Screenshots → `screenshots/` folder
- Report → `reports/` folder
- Log updates → `logs/` folder

### C2 — Push to GitHub
Open terminal inside the project folder and run:

```bash
# Step 1: See what files you changed
git status

# Step 2: Stage your files
git add .

# Step 3: Write a short message describing what you did
git commit -m "Add task4_cleaning notebook - Sri Lakshmi"

# Step 4: Push to GitHub
git push origin main
```

> If it asks for a username/password, use your GitHub username and a **Personal Access Token** (not your password). Generate one at: GitHub → Settings → Developer Settings → Personal Access Tokens → Tokens (classic) → Generate new token → tick `repo` → copy it.

### C3 — Pull before you start working (avoid conflicts)
Every time you sit down to work, first run:
```bash
git pull origin main
```
This makes sure you have everyone else's latest changes before you start.

---

## SECTION D — REPO FILE NAMING RULES (Everyone must follow this)

| File | Person | Where to put it |
|------|--------|-----------------|
| `task4_cleaning.ipynb` | Sri Lakshmi | `notebooks/` |
| `task5_eda.ipynb` | Deepesh | `notebooks/` |
| `genre_distribution.png` | Sri Lakshmi | `notebooks/` |
| `eda_plot_1.png` to `eda_plot_4.png` | Deepesh | `notebooks/` |
| HDFS screenshots | Jeevan | `screenshots/` |
| `work_division.md` | Jeevan | `logs/` |
| `meetings_log.md` | All | `logs/` |
| Final report PDF/DOCX | Jeevan | `reports/` |

> ⚠️ Do NOT push `spotify_tracks.csv` or `spotify_cleaned.csv` to GitHub — they are too large. Keep them only on your local machine and share via Google Drive or any file sharing app.

---

## ✅ CROSS-CHECK WITH INSTRUCTOR REQUIREMENTS

| Requirement | What We're Doing | Status |
|---|---|---|
| ≥ 100,000 rows | Spotify dataset has ~600,000 rows | ✅ |
| N ML problem statements (N=3) | 3 ML tasks defined | ✅ |
| 2N data analysis objectives (2×3=6) | 6 objectives defined | ✅ |
| 2N cleaning operations (2×3=6) | 6 cleaning steps in notebook | ✅ |
| 2N EDA operations (2×3=6) | 6 EDA steps (mix graphical + non-graphical) | ✅ |
| Jupyter Notebook as environment | All code in .ipynb files | ✅ |
| HDFS raw dataset (Part A) | Raw CSV uploaded to /spotify/raw/ | ✅ |
| HDFS cleaned dataset (Part B) | Cleaned CSV uploaded to /spotify/cleaned/ | ✅ |
| Written report | All tasks documented in report | ✅ |
| Reproducible pipeline | Notebooks run top-to-bottom without errors | ✅ |

---

## ⚡ WORK DIVISION AT A GLANCE

| Person | Tasks | Points |
|---|---|---|
| **Jeevan** | Task 1 (Problem Statement) + Task 3 (HDFS Setup) + Dataset Download | 35 pts |
| **Sri Lakshmi** | Task 2 (Data Sources) + Task 4 (Data Cleaning) | 40 pts |
| **Deepesh** | Task 5 (EDA) | 25 pts |

### ⚠️ ORDER MATTERS — Follow this sequence:
1. Jeevan starts HDFS setup + writes Problem Statement + downloads dataset (simultaneously)
2. Jeevan hands off `spotify_tracks.csv` to Sri Lakshmi
3. Sri Lakshmi runs the cleaning notebook and produces `spotify_cleaned.csv`
4. Sri Lakshmi hands off `spotify_cleaned.csv` to Deepesh AND to Jeevan
5. Deepesh runs EDA notebook
6. Jeevan uploads `spotify_cleaned.csv` to HDFS last

---

## 🕐 TIMELINE (1 Day)

| Time | Jeevan | Sri Lakshmi | Deepesh |
|---|---|---|---|
| Hour 0–1 | Write Problem Statement + download dataset from Kaggle | Install Jupyter + dependencies | Install dependencies |
| Hour 1–3 | Docker + HDFS setup, upload raw CSV, hand off spotify_tracks.csv to Sri Lakshmi | Wait for CSV, then run cleaning notebook | Wait for cleaned CSV |
| Hour 3–5 | Wait / help team | Finish cleaning, hand off spotify_cleaned.csv to Deepesh + Jeevan | Run EDA notebook |
| Hour 5–6 | Upload cleaned CSV to HDFS | Compile report section | Compile report section |
| Hour 6+ | Everyone assembles the final report together | | |

---

---

# 👤 JEEVAN'S TASKS

## TASK 1 — Problem Statement [20 pts]
*Write all of this in your report. You do NOT need a notebook for this task.*

---

### Project Title
> "Predicting Track Popularity and Discovering Music Patterns Using the Spotify Tracks Dataset"

---

### High-Level Problem Statement
Write this in your report:

Music streaming platforms serve billions of listeners worldwide and need to understand what makes a track popular in order to power recommendation engines, playlist curation, and artist discovery tools. This project analyzes the Spotify Tracks Dataset — approximately 600,000 tracks with rich audio features and popularity scores provided directly by Spotify — to uncover what audio and metadata features drive track popularity, segment music into natural clusters, and build predictive models.

**Stakeholders who benefit from this analysis:**
- Streaming platforms (Spotify, Apple Music) optimizing recommendation systems
- Independent artists wanting to understand what makes a track more likely to succeed
- Record labels identifying hit potential before investing in promotion
- Music recommendation system engineers building AI-powered features

---

### ML Problem Statements (N=3 — one per team member, all go in report)

**ML Task 1 — Regression (Team Member 1):**
Predict a track's popularity score (a continuous value from 0 to 100) using its audio features such as danceability, energy, loudness, tempo, valence, acousticness, and instrumentalness.
- Input: Audio feature vector per track
- Output: Continuous popularity score (float 0–100)
- Unit of analysis: Per track

**ML Task 2 — Classification (Team Member 2):**
Classify each track into one of three popularity tiers — Low (0–33), Medium (34–66), or High (67–100) — using its audio features and genre.
- Input: Audio features + track_genre
- Output: 3-class label (low / medium / high)
- Unit of analysis: Per track

**ML Task 3 — Clustering / Unsupervised Learning (Team Member 3):**
Group tracks into natural "mood and vibe" clusters using audio features only, with no labels. The goal is to discover whether distinct musical archetypes (e.g., energetic dance tracks, calm acoustic tracks, intense rock tracks) emerge naturally from the data.
- Input: Normalized audio feature vector (danceability, energy, valence, tempo, acousticness, etc.)
- Output: Cluster ID (integer) assigned to each track
- Unit of analysis: Per track

---

### Data Analysis Objectives (2N = 6 objectives, all go in report)

1. Understand the distribution of track popularity across different genres and identify which genres consistently produce high-popularity tracks.
2. Identify which audio features (danceability, energy, loudness, valence, tempo) have the strongest statistical correlation with track popularity.
3. Analyze how musical characteristics such as tempo, energy, and acousticness have shifted across release decades (e.g., 1960s vs 1990s vs 2020s).
4. Compare danceability and energy profiles across genres to understand the genre-specific audio fingerprint that defines each genre.
5. Identify the most prolific and highest-popularity artists in the dataset and examine what audio features distinguish their tracks from lower-popularity tracks.
6. Examine the relationship between track duration and popularity to determine whether listener attention span affects streaming performance.

---

### Input → Output Specification
Write this in your report:

**Input data:** spotify_tracks.csv
**Key fields used:** track_id, artists, track_genre, release_year, popularity, danceability, energy, loudness, speechiness, acousticness, instrumentalness, liveness, valence, tempo, duration_minutes, explicit

**Outputs:**
- Regression model → predicted popularity score (float)
- Classification model → popularity tier label (low / medium / high)
- Clustering model → cluster ID per track (integer)

All outputs are at the **per-track level**.

---

---

## TASK 3 — HDFS Setup & Ingestion [15 pts]
*This is the most technical part. Follow every step exactly.*

### STEP 1 — Install Docker Desktop
1. Go to: **https://www.docker.com/products/docker-desktop**
2. Download for your operating system (Windows / Mac / Linux)
3. Install it and open Docker Desktop
4. Wait until the bottom-left says **"Docker is running"** (green dot)

---

### STEP 2 — Pull and Start Hadoop Container
Open your terminal (Command Prompt on Windows, Terminal on Mac/Linux) and run:

```bash
docker pull sequenceiq/hadoop-docker:2.7.1
```

Wait for it to finish downloading. Then run:

```bash
docker run -it -p 50070:50070 -p 9000:9000 \
  --name hadoop_phase1 \
  sequenceiq/hadoop-docker:2.7.1 /etc/bootstrap.sh -bash
```

Wait until you see a bash prompt that looks like this: `bash-4.1#`
📸 **TAKE A SCREENSHOT of this screen. You need it for the report.**

---

### STEP 3 — Create the HDFS Folder Structure
You are now inside the Docker container. Run these commands:

```bash
hdfs dfs -mkdir -p /spotify/raw
hdfs dfs -mkdir -p /spotify/cleaned
hdfs dfs -ls /spotify
```

You should see `/spotify/raw` and `/spotify/cleaned` listed.
📸 **TAKE A SCREENSHOT of the output of `hdfs dfs -ls /spotify`**

---

### STEP 4 — Download the Dataset from Kaggle
1. Go to: **https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset**
2. Create a free Kaggle account if you don't have one
3. Click Download
4. The file will be called `dataset.csv` — **rename it to `spotify_tracks.csv`**

---

### STEP 5 — Copy Raw CSV into HDFS
Open a **NEW terminal window** (keep the Docker container open in the first one).

In the new terminal, run (replace the path with where your file actually is):

```bash
# On Mac/Linux:
docker cp /Users/yourname/Downloads/spotify_tracks.csv hadoop_phase1:/root/

# On Windows (Command Prompt):
docker cp C:\Users\yourname\Downloads\spotify_tracks.csv hadoop_phase1:/root/
```

Then go back to your Docker terminal and run:

```bash
hdfs dfs -put /root/spotify_tracks.csv /spotify/raw/
hdfs dfs -ls /spotify/raw/
```

You should see `spotify_tracks.csv` listed with its file size.
📸 **TAKE A SCREENSHOT of this output. This is your Part A HDFS proof.**

---

### STEP 6 — Upload Cleaned CSV (Do this AFTER Sri Lakshmi finishes)
Once Sri Lakshmi gives you `spotify_cleaned.csv`, run:

```bash
# In a new local terminal:
docker cp /path/to/spotify_cleaned.csv hadoop_phase1:/root/

# Back in Docker terminal:
hdfs dfs -put /root/spotify_cleaned.csv /spotify/cleaned/
hdfs dfs -ls /spotify/cleaned/
```

📸 **TAKE A SCREENSHOT of this output. This is your Part B HDFS proof.**

---

### What to Include in the Report for Task 3
- All the commands above (copy them exactly)
- Screenshot 1: Docker container running (bash prompt visible)
- Screenshot 2: `hdfs dfs -ls /spotify` showing both folders
- Screenshot 3: `hdfs dfs -ls /spotify/raw/` showing spotify_tracks.csv
- Screenshot 4: `hdfs dfs -ls /spotify/cleaned/` showing spotify_cleaned.csv

---

---

# 👤 SRI LAKSHMI'S TASKS

---
> ## 🚨 SRI LAKSHMI — READ THIS BEFORE YOU TOUCH ANYTHING
>
> **1. Join the Teams workspace first.**
> Jeevan will send you an invite link to Microsoft Teams. Accept it before doing anything else. All updates, file handoffs, and questions go there.
>
> **2. Clone the GitHub repo.**
> Follow Section B in the Team Setup at the top of this document. Do this before writing a single line of code.
>
> **3. Do NOT start until Jeevan sends you `spotify_tracks.csv`.**
> Wait for the file. Do not download anything yourself.
>
> **4. Post an update in Teams after EVERY operation you finish.**
> Example: *"Done with Operation 2 — removed 150 null rows"*. Jeevan and Deepesh need to know your progress.
>
> **5. When you finish, post `spotify_cleaned.csv` in the `#file-handoffs` Teams channel.**
> Both Jeevan and Deepesh are waiting for this file. Do not send it on WhatsApp or email — use Teams only so there is a record.
>
> **6. Push your notebook to GitHub when done.**
> Put `task4_cleaning.ipynb` in the `notebooks/` folder and follow Section C (git add → commit → push).
>
> **7. If you get an error, paste it in the `#task-4-cleaning` Teams channel immediately.**
> Do not sit on it. Someone will help you fast.
---

## TASK 2 — Data Sources [15 pts] + TASK 4 — Data Cleaning [25 pts]

### Before You Start:
1. **Get `spotify_tracks.csv` from Jeevan** — he will download it and send it to you directly. Do not start until you have this file.
2. Install Jupyter and required libraries by running in your terminal:
   ```
   pip install notebook pandas matplotlib seaborn
   ```
3. Launch Jupyter: run `jupyter notebook` in your terminal
4. Place `spotify_tracks.csv` in the same folder where you create your notebook
5. Create a new notebook called `task4_cleaning.ipynb`

---

## 🤖 STEP 1 — PASTE THIS ENTIRE PROMPT INTO CLAUDE ON YOUR MACHINE

> Open Claude (claude.ai), paste everything inside the box below, and hit send. Claude will guide you through every single step with zero errors.

```
You are helping me complete Task 2 (Data Sources) and Task 4 (Data Cleaning) for a university big data course project called Phase 1.

== PROJECT CONTEXT ==
- Topic: Spotify Tracks Dataset — Music Popularity and Audio Feature Analysis
- Dataset file I already have: spotify_tracks.csv (given to me by my teammate)
- Team size: 3 people. N=3, so we need exactly 6 cleaning operations total.
- Environment: Jupyter Notebook (local), Python
- Libraries allowed: pandas, matplotlib, seaborn only (no sklearn — that is for Phase 2)

== TASK 2 — DATA SOURCES REPORT SECTION ==
Write a professional report section titled "2. Data Sources" that includes:
- Full citation: PandyaM. (2022). Spotify Tracks Dataset. Kaggle. https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset
- Description of what the dataset contains: ~600,000 Spotify tracks, 125+ genres, spanning multiple decades
- Key columns: track_id, artists, track_name, track_album_name, track_album_release_date, playlist_genre, playlist_subgenre, track_genre, popularity, duration_ms, explicit, danceability, energy, key, loudness, mode, speechiness, acousticness, instrumentalness, liveness, valence, tempo
- Why this dataset fits our problem (music popularity prediction + audio feature analysis)
- Confirmation that it exceeds the 100,000 row minimum requirement

== TASK 4 — DATA CLEANING NOTEBOOK ==
Create a complete, runnable Jupyter Notebook called task4_cleaning.ipynb.
For each of the 6 operations below, generate:
1. A markdown cell explaining WHAT we are doing and WHY
2. The full Python code cell (follow the sample style shown below exactly)
3. A markdown cell showing before/after result or what to expect

Here are the exact 6 operations in order:

OPERATION 1 — Load and Inspect the Dataset
- Import pandas, matplotlib.pyplot, seaborn
- Load spotify_tracks.csv using pandas
- Print shape, dtypes, first 5 rows, and df.describe()
Sample style:
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
df = pd.read_csv('spotify_tracks.csv')
print("Shape:", df.shape)
print("\nData Types:")
print(df.dtypes)
print("\nFirst 5 rows:")
df.head()

OPERATION 2 — Handle Missing Values
- Count and display nulls per column as a table
- Drop rows where artists, track_name, or track_genre is null
- Print how many rows were removed and how many remain
Sample style:
print("Missing values per column:")
print(df.isnull().sum())
rows_before = len(df)
df = df.dropna(subset=['artists', 'track_name', 'track_genre'])
rows_after = len(df)
print(f"\nRows removed: {rows_before - rows_after}")
print(f"Rows remaining: {rows_after}")

OPERATION 3 — Remove Duplicate Tracks
- Find and remove duplicate rows based on track_id column, keep first occurrence
- Print count before and after
Sample style:
rows_before = len(df)
df = df.drop_duplicates(subset='track_id', keep='first')
rows_after = len(df)
print(f"Duplicates removed: {rows_before - rows_after}")
print(f"Rows remaining: {rows_after}")

OPERATION 4 — Fix Data Types and Derive New Columns
- Convert duration_ms to duration_minutes by dividing by 60000, round to 2 decimals
- Parse track_album_release_date to datetime using pd.to_datetime with errors='coerce'
- Extract release_year as a new integer column from the datetime
- Drop the original duration_ms column
Sample style:
df['duration_minutes'] = (df['duration_ms'] / 60000).round(2)
df = df.drop(columns=['duration_ms'])
df['track_album_release_date'] = pd.to_datetime(df['track_album_release_date'], errors='coerce')
df['release_year'] = df['track_album_release_date'].dt.year.astype('Int64')
print("New columns added: duration_minutes, release_year")
print(df[['duration_minutes', 'release_year']].head())

OPERATION 5 — Flag Zero-Popularity Tracks
- Create a new boolean column called is_zero_popularity that is True when popularity == 0
- Print how many tracks have zero popularity and what percentage that is of the total
- Print df['popularity'].describe()
Sample style:
df['is_zero_popularity'] = df['popularity'] == 0
zero_count = df['is_zero_popularity'].sum()
total = len(df)
print(f"Zero-popularity tracks: {zero_count} ({100*zero_count/total:.1f}% of dataset)")
print(df['popularity'].describe())

OPERATION 6 — Normalize track_genre Column
- Strip whitespace and convert track_genre to lowercase using .str.strip().str.lower()
- Print unique genre count before and after
- Plot top 15 genres by track count as a bar chart, save as genre_distribution.png
Sample style:
print(f"Unique genres before: {df['track_genre'].nunique()}")
df['track_genre'] = df['track_genre'].str.strip().str.lower()
print(f"Unique genres after: {df['track_genre'].nunique()}")
top_genres = df['track_genre'].value_counts().head(15)
plt.figure(figsize=(10,6))
top_genres.plot(kind='bar', color='steelblue')
plt.title('Top 15 Genres by Track Count')
plt.xlabel('Genre')
plt.ylabel('Number of Tracks')
plt.xticks(rotation=45, ha='right')
plt.tight_layout()
plt.savefig('genre_distribution.png')
plt.show()

FINAL STEP — Save the Cleaned Dataset
Sample style:
df.to_csv('spotify_cleaned.csv', index=False)
print(f"Cleaned dataset saved as spotify_cleaned.csv")
print(f"Final shape: {df.shape}")

== IMPORTANT RULES ==
- Every single cell must run without any errors
- Use clear markdown headers between each section
- The notebook must be fully self-contained — someone else should be able to run it top to bottom
- Match the sample style exactly — same variable names, same print messages, same file names
- At the very end, tell me exactly what files were produced and what I need to hand off to my teammates

Please start by writing the Task 2 report text first, then build the notebook cell by cell.
```

---

## 📋 STEP 2 — SAMPLE REFERENCE CODE
> This is the exact code Claude should generate. Use this to verify Claude's output matches what we expect. If Claude gives you something different, show it this and say "match this style exactly."

---

**OPERATION 1 — Load and Inspect**
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv('spotify_tracks.csv')

print("Shape:", df.shape)
print("\nData Types:")
print(df.dtypes)
print("\nFirst 5 rows:")
df.head()
```

---

**OPERATION 2 — Handle Missing Values**
```python
print("Missing values per column:")
print(df.isnull().sum())

rows_before = len(df)
df = df.dropna(subset=['artists', 'track_name', 'track_genre'])
rows_after = len(df)

print(f"\nRows removed: {rows_before - rows_after}")
print(f"Rows remaining: {rows_after}")
```

---

**OPERATION 3 — Remove Duplicate Tracks**
```python
rows_before = len(df)
df = df.drop_duplicates(subset='track_id', keep='first')
rows_after = len(df)

print(f"Duplicates removed: {rows_before - rows_after}")
print(f"Rows remaining: {rows_after}")
```

---

**OPERATION 4 — Fix Data Types**
```python
df['duration_minutes'] = (df['duration_ms'] / 60000).round(2)
df = df.drop(columns=['duration_ms'])

df['track_album_release_date'] = pd.to_datetime(df['track_album_release_date'], errors='coerce')
df['release_year'] = df['track_album_release_date'].dt.year.astype('Int64')

print("New columns added: duration_minutes, release_year")
print(df[['duration_minutes', 'release_year']].head())
```

---

**OPERATION 5 — Flag Zero-Popularity Tracks**
```python
df['is_zero_popularity'] = df['popularity'] == 0

zero_count = df['is_zero_popularity'].sum()
total = len(df)
print(f"Zero-popularity tracks: {zero_count} ({100*zero_count/total:.1f}% of dataset)")
print(df['popularity'].describe())
```

---

**OPERATION 6 — Normalize track_genre**
```python
print(f"Unique genres before: {df['track_genre'].nunique()}")

df['track_genre'] = df['track_genre'].str.strip().str.lower()

print(f"Unique genres after: {df['track_genre'].nunique()}")

top_genres = df['track_genre'].value_counts().head(15)
plt.figure(figsize=(10,6))
top_genres.plot(kind='bar', color='steelblue')
plt.title('Top 15 Genres by Track Count')
plt.xlabel('Genre')
plt.ylabel('Number of Tracks')
plt.xticks(rotation=45, ha='right')
plt.tight_layout()
plt.savefig('genre_distribution.png')
plt.show()
```

---

**FINAL STEP — Save Cleaned Dataset**
```python
df.to_csv('spotify_cleaned.csv', index=False)
print(f"Cleaned dataset saved as spotify_cleaned.csv")
print(f"Final shape: {df.shape}")
```

---

### 📤 Hand Off:
Once this notebook runs without errors, send `spotify_cleaned.csv` to:
- **Deepesh** (for EDA — Task 5)
- **Jeevan** (to upload to HDFS /spotify/cleaned/)

---

---

# 👤 DEEPESH'S TASKS

---
> ## 🚨 DEEPESH — READ THIS BEFORE YOU TOUCH ANYTHING
>
> **1. Join the Teams workspace first.**
> Jeevan will send you an invite link to Microsoft Teams. Accept it before doing anything else. All updates, file handoffs, and questions go there.
>
> **2. Clone the GitHub repo.**
> Follow Section B in the Team Setup at the top of this document. Do this before writing a single line of code.
>
> **3. Do NOT start until Sri Lakshmi posts `spotify_cleaned.csv` in the `#file-handoffs` Teams channel.**
> Wait for that file. Your entire notebook depends on it. Starting without it will waste your time.
>
> **4. Post an update in Teams after EVERY operation you finish.**
> Example: *"Done with EDA Operation 3 — popularity histogram saved as eda_plot_1.png"*. Jeevan needs to know your progress to compile the report.
>
> **5. When you finish, post all 4 chart images + your notebook in the `#file-handoffs` Teams channel.**
> Jeevan needs: `task5_eda.ipynb`, `eda_plot_1.png`, `eda_plot_2.png`, `eda_plot_3.png`, `eda_plot_4.png`.
>
> **6. Push your notebook to GitHub when done.**
> Put `task5_eda.ipynb` and all 4 plot images in the `notebooks/` folder and follow Section C (git add → commit → push).
>
> **7. If you get an error, paste it in the `#task-5-eda` Teams channel immediately.**
> Do not sit on it. Someone will help you fast.
---

## TASK 5 — Exploratory Data Analysis [25 pts]

### Before You Start:
1. Get `spotify_cleaned.csv` from Sri Lakshmi — **do not start until you have this file**
2. Install dependencies:
   ```
   pip install notebook pandas matplotlib seaborn numpy
   ```
3. Launch Jupyter: run `jupyter notebook` in terminal
4. Create a new notebook called `task5_eda.ipynb`
5. Put `spotify_cleaned.csv` in the same folder as the notebook

---

## 🤖 STEP 1 — PASTE THIS ENTIRE PROMPT INTO CLAUDE ON YOUR MACHINE

> Open Claude (claude.ai), paste everything inside the box below, and hit send. Claude will guide you through every single step with zero errors.

```
You are helping me complete Task 5 (Exploratory Data Analysis) for a university big data course project called Phase 1.

== PROJECT CONTEXT ==
- Topic: Spotify Tracks Dataset — Music Popularity and Audio Feature Analysis
- My input file: spotify_cleaned.csv (given to me by my teammate Sri Lakshmi)
- Team size: 3 people. N=3, so we need exactly 6 EDA operations total.
- Environment: Jupyter Notebook (local), Python
- Libraries allowed: pandas, matplotlib, seaborn, numpy only (no sklearn — that is for Phase 2)

== CLEANED DATASET COLUMNS ==
track_id, artists, track_name, track_album_name, track_album_release_date, release_year,
playlist_name, playlist_genre, playlist_subgenre, popularity, is_zero_popularity,
duration_minutes, explicit, danceability, energy, key, loudness, mode, speechiness,
acousticness, instrumentalness, liveness, valence, tempo, track_genre

== YOUR JOB ==
Create a complete, runnable Jupyter Notebook called task5_eda.ipynb.
For each of the 6 EDA operations below, generate:
1. A markdown cell explaining: what this analysis is, what it reveals, why it matters for Phase 2 modeling
2. The full Python code cell (follow the sample style shown below exactly)
3. A markdown interpretation cell with guiding questions to fill in after running

EDA OPERATION 1 — Summary Statistics (Non-graphical)
- Import pandas, matplotlib.pyplot, seaborn, numpy and load spotify_cleaned.csv
- Run df.describe().round(2) and display it
- Compute skewness and kurtosis for: popularity, danceability, energy, tempo, duration_minutes
Sample style:
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
df = pd.read_csv('spotify_cleaned.csv')
print("=== Descriptive Statistics ===")
print(df.describe().round(2))
print("\n=== Skewness and Kurtosis ===")
cols = ['popularity', 'danceability', 'energy', 'tempo', 'duration_minutes']
for col in cols:
    print(f"{col}: skewness={df[col].skew():.3f}, kurtosis={df[col].kurtosis():.3f}")

EDA OPERATION 2 — Missingness and Zero-Popularity Analysis (Non-graphical)
- Show remaining null counts per column
- Calculate percentage of tracks where is_zero_popularity == True
- Compute mean popularity for zero vs non-zero tracks using groupby
Sample style:
print("=== Remaining Null Values ===")
print(df.isnull().sum())
zero_pct = 100 * df['is_zero_popularity'].sum() / len(df)
print(f"\nPercentage of zero-popularity tracks: {zero_pct:.1f}%")
print("\n=== Mean Popularity: Zero vs Non-Zero ===")
print(df.groupby('is_zero_popularity')['popularity'].mean())

EDA OPERATION 3 — Popularity Distribution (Graphical)
- Histogram of popularity with bins=50 and KDE overlay, mean line (red), median line (orange)
- Save as eda_plot_1.png
Sample style:
plt.figure(figsize=(10, 5))
sns.histplot(df['popularity'], bins=50, kde=True, color='steelblue')
plt.axvline(df['popularity'].mean(), color='red', linestyle='--', label=f"Mean: {df['popularity'].mean():.1f}")
plt.axvline(df['popularity'].median(), color='orange', linestyle='--', label=f"Median: {df['popularity'].median():.1f}")
plt.title('Distribution of Track Popularity')
plt.xlabel('Popularity Score')
plt.ylabel('Number of Tracks')
plt.legend()
plt.tight_layout()
plt.savefig('eda_plot_1.png')
plt.show()

EDA OPERATION 4 — Correlation Heatmap (Graphical)
- Pearson correlation matrix for: popularity, danceability, energy, loudness, speechiness,
  acousticness, instrumentalness, liveness, valence, tempo, duration_minutes
- Plot as seaborn heatmap, save as eda_plot_2.png
Sample style:
feature_cols = ['popularity', 'danceability', 'energy', 'loudness', 'speechiness',
                'acousticness', 'instrumentalness', 'liveness', 'valence', 'tempo', 'duration_minutes']
corr = df[feature_cols].corr()
plt.figure(figsize=(12, 9))
sns.heatmap(corr, annot=True, fmt=".2f", cmap='coolwarm', square=True, linewidths=0.5)
plt.title('Correlation Heatmap: Audio Features vs Popularity')
plt.tight_layout()
plt.savefig('eda_plot_2.png')
plt.show()

EDA OPERATION 5 — Top Genres by Average Popularity (Graphical)
- Mean popularity per track_genre, top 15, horizontal bar chart, save as eda_plot_3.png
Sample style:
top_genres = (df.groupby('track_genre')['popularity'].mean().sort_values(ascending=False).head(15))
plt.figure(figsize=(10, 7))
colors = sns.color_palette("Blues_r", len(top_genres))
top_genres.plot(kind='barh', color=colors)
plt.title('Top 15 Genres by Average Track Popularity')
plt.xlabel('Average Popularity Score')
plt.ylabel('Genre')
plt.gca().invert_yaxis()
plt.tight_layout()
plt.savefig('eda_plot_3.png')
plt.show()

EDA OPERATION 6 — Danceability vs Popularity Scatter (Graphical)
- Sample 5000 rows, scatter x=danceability y=popularity colored by energy, trend line, save as eda_plot_4.png
Sample style:
sample = df.sample(5000, random_state=42)
plt.figure(figsize=(10, 6))
scatter = plt.scatter(sample['danceability'], sample['popularity'], c=sample['energy'], cmap='RdYlGn', alpha=0.5, s=10)
plt.colorbar(scatter, label='Energy Level')
z = np.polyfit(sample['danceability'], sample['popularity'], 1)
p = np.poly1d(z)
x_line = np.linspace(0, 1, 100)
plt.plot(x_line, p(x_line), color='navy', linewidth=2, label='Trend line')
plt.title('Danceability vs Popularity (colored by Energy)')
plt.xlabel('Danceability')
plt.ylabel('Popularity')
plt.legend()
plt.tight_layout()
plt.savefig('eda_plot_4.png')
plt.show()

FINAL SUMMARY CELL
- Add a final markdown cell titled 'EDA Summary and Implications for Phase 2'
- Include 6 bullet points, one per operation, with [fill in after running] placeholders for numbers

== IMPORTANT RULES ==
- Every single cell must run without any errors on spotify_cleaned.csv
- All plots must have: title, axis labels, plt.tight_layout(), and be saved as .png files
- Match the sample style exactly — same variable names, same file names, same print messages
- The notebook must be fully self-contained
- At the very end, tell me exactly what files were produced and what to hand off to Jeevan

Please build the notebook cell by cell, one operation at a time.
```

---

## 📋 STEP 2 — SAMPLE REFERENCE CODE
> This is the exact code Claude should generate. Use this to verify Claude's output matches. If Claude gives you something different, show it this and say "match this style exactly."

---

**EDA OPERATION 1 — Summary Statistics**
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

df = pd.read_csv('spotify_cleaned.csv')

print("=== Descriptive Statistics ===")
print(df.describe().round(2))

print("\n=== Skewness and Kurtosis for Key Columns ===")
cols = ['popularity', 'danceability', 'energy', 'tempo', 'duration_minutes']
for col in cols:
    print(f"{col}: skewness={df[col].skew():.3f}, kurtosis={df[col].kurtosis():.3f}")
```

---

**EDA OPERATION 2 — Missingness and Zero-Popularity Analysis**
```python
print("=== Remaining Null Values ===")
print(df.isnull().sum())

zero_pct = 100 * df['is_zero_popularity'].sum() / len(df)
print(f"\nPercentage of zero-popularity tracks: {zero_pct:.1f}%")

print("\n=== Mean Popularity: Zero vs Non-Zero ===")
print(df.groupby('is_zero_popularity')['popularity'].mean())
```

---

**EDA OPERATION 3 — Popularity Distribution**
```python
plt.figure(figsize=(10, 5))
sns.histplot(df['popularity'], bins=50, kde=True, color='steelblue')
plt.axvline(df['popularity'].mean(), color='red', linestyle='--', label=f"Mean: {df['popularity'].mean():.1f}")
plt.axvline(df['popularity'].median(), color='orange', linestyle='--', label=f"Median: {df['popularity'].median():.1f}")
plt.title('Distribution of Track Popularity')
plt.xlabel('Popularity Score')
plt.ylabel('Number of Tracks')
plt.legend()
plt.tight_layout()
plt.savefig('eda_plot_1.png')
plt.show()
```

---

**EDA OPERATION 4 — Correlation Heatmap**
```python
feature_cols = ['popularity', 'danceability', 'energy', 'loudness',
                'speechiness', 'acousticness', 'instrumentalness',
                'liveness', 'valence', 'tempo', 'duration_minutes']

corr = df[feature_cols].corr()

plt.figure(figsize=(12, 9))
sns.heatmap(corr, annot=True, fmt=".2f", cmap='coolwarm', square=True, linewidths=0.5)
plt.title('Correlation Heatmap: Audio Features vs Popularity')
plt.tight_layout()
plt.savefig('eda_plot_2.png')
plt.show()
```

---

**EDA OPERATION 5 — Top Genres by Average Popularity**
```python
top_genres = (df.groupby('track_genre')['popularity']
              .mean()
              .sort_values(ascending=False)
              .head(15))

plt.figure(figsize=(10, 7))
colors = sns.color_palette("Blues_r", len(top_genres))
top_genres.plot(kind='barh', color=colors)
plt.title('Top 15 Genres by Average Track Popularity')
plt.xlabel('Average Popularity Score')
plt.ylabel('Genre')
plt.gca().invert_yaxis()
plt.tight_layout()
plt.savefig('eda_plot_3.png')
plt.show()
```

---

**EDA OPERATION 6 — Danceability vs Popularity Scatter**
```python
sample = df.sample(5000, random_state=42)

plt.figure(figsize=(10, 6))
scatter = plt.scatter(sample['danceability'], sample['popularity'],
                      c=sample['energy'], cmap='RdYlGn', alpha=0.5, s=10)
plt.colorbar(scatter, label='Energy Level')

z = np.polyfit(sample['danceability'], sample['popularity'], 1)
p = np.poly1d(z)
x_line = np.linspace(0, 1, 100)
plt.plot(x_line, p(x_line), color='navy', linewidth=2, label='Trend line')

plt.title('Danceability vs Popularity (colored by Energy)')
plt.xlabel('Danceability')
plt.ylabel('Popularity')
plt.legend()
plt.tight_layout()
plt.savefig('eda_plot_4.png')
plt.show()
```

---

### 📤 Hand Off:
Once your notebook runs without errors, send to Jeevan:
- `task5_eda.ipynb` — the full EDA notebook
- `eda_plot_1.png` through `eda_plot_4.png` — the four saved charts
- The "EDA Summary" markdown cell content → paste into the team report

---

---

# 📄 FINAL REPORT STRUCTURE

When assembling the final report, structure it exactly like this:

```
1. Problem Statement
   - Project title
   - High-level problem statement + stakeholders
   - 3 ML problem statements (one per team member)
   - 6 data analysis objectives
   - Input → Output specification

2. Data Sources
   - Dataset citation and link
   - Dataset description (columns, size, time span)
   - Justification for dataset choice

3. Hadoop / HDFS
   - HDFS commands used
   - Screenshot: Hadoop running in Docker
   - Screenshot: /spotify/raw/ with raw CSV
   - Screenshot: /spotify/cleaned/ with cleaned CSV

4. Data Cleaning
   - Paste from task4_cleaning.ipynb (all 6 operations with markdown explanations)

5. Exploratory Data Analysis
   - Paste from task5_eda.ipynb (all 6 operations with plots and interpretations)
   - Include the 4 saved plot images
```

---

# 📌 IMPORTANT REMINDERS

- **Phase Lock:** After Phase 1 submission you cannot change your dataset or problem. Phase 2 builds on this exactly.
- **Raw data must stay in HDFS** even after uploading the cleaned version. Do not delete it.
- **Jupyter Notebooks** are required — do not submit plain .py files for Tasks 4 and 5.
- **GitHub repo:** Set up a shared repo, invite all members and the TA. Commit all notebooks, CSVs, and screenshots.
- **Work Division file:** Create a text file listing who did what and have all 3 members sign off on it.
- **Meetings Log:** Keep a short log of when you met and what was decided.