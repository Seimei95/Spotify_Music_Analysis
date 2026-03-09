# 🎵 Spotify Music Analysis — Phase 1 Complete Team Plan
**Course Project | Big Data Pipeline | Hadoop + Python**
**Dataset:** Spotify Tracks Dataset (Kaggle, ~114,000 rows)
**Team Size:** 3 people | N = 3
**Internal Working Deadline:** 1 Day | **Submission Deadline:** March 14, 2026 (Saturday) 11:59 PM EST via UBLearns

---

## 📌 QUICK NAVIGATION
**Jump To**
[🛠️ Team Setup — GitHub, Teams, Repo](#-team-setup--do-this-before-anything-else)
[A. Jeevan — Repo Setup, Teams, Work Division](#section-a--jeevan-sets-up-the-repo-do-this-first-alone)
[B. Sri Lakshmi + Deepesh — Clone Repo](#section-b--sri-lakshmi-and-deepesh-clone-the-repo-each-person-does-this-on-their-own-machine)
[C. How to Push Work to GitHub](#section-c--how-to-submit-your-work-all-three-members-follow-this-every-time)
[D. File Naming Rules](#section-d--repo-file-naming-rules-everyone-must-follow-this)
[✅ Instructor Requirements Checklist](#-cross-check-with-instructor-requirements)
[⚡ Work Division at a Glance](#-work-division-at-a-glance)
[🕐 Timeline — 1 Day](#-timeline-1-day)
[👤 Jeevan's Tasks — Task 1 + Task 3](#-jeevans-tasks)
[👤 Sri Lakshmi's Tasks — Task 2 + Task 4](#-sri-lakshmis-tasks)
[👤 Deepesh's Tasks — Task 5 EDA](#-deepeshs-tasks)
[📄 Final Report Structure](#-final-report-structure)
[📌 Important Reminders](#-important-reminders)

---

## 🛠️ TEAM SETUP — DO THIS BEFORE ANYTHING ELSE
**Jeevan handles all of Section A. Sri Lakshmi and Deepesh only do Section B and C on their own machines.**

### SECTION A — JEEVAN SETS UP THE REPO (Do this first, alone)

**A1 — Prepare the GitHub Repository**
Your repo is already created at: `https://github.com/Seimei95/Spotify_Music_Analysis.git`

1. Go to your repo on GitHub
2. Create the following folder structure by adding a blank `.gitkeep` file inside each folder:
```text
Spotify_Music_Analysis/
├── notebooks/          ← Sri Lakshmi and Deepesh put their .ipynb files here
├── data/               ← DO NOT push CSVs here (too large). Just a placeholder.
├── screenshots/        ← All HDFS screenshots go here
├── reports/            ← Final compiled report goes here
├── logs/               ← Work Division file and Meetings Log go here
└── README.md           ← Already exists or create it
```
*(In each empty folder, create a file called `.gitkeep` with no content so GitHub tracks the folder)*

**A2 — Invite Teammates to GitHub**

1. Go to your repo: `https://github.com/Seimei95/Spotify_Music_Analysis`
2. Click **Settings → Collaborators → Add people**
3. Add Sri Lakshmi and Deepesh by their GitHub usernames or email addresses
4. Also add your TA as a collaborator (ask your TA for their GitHub username)
5. Set all of them to **Write** access

**A3 — Create the Work Division File**
In the `logs/` folder, create a file called `work_division.md` and paste this:

```md
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

**A4 — Create the Meetings Log File**
In the `logs/` folder, create a file called `meetings_log.md` and paste this:

```md
# Meetings Log — Spotify Music Analysis Phase 1

## Meeting 1
Date: [fill in today's date]
Attendees: Jeevan, Sri Lakshmi, Deepesh
Discussion: Agreed on project topic (Spotify dataset), divided tasks, set up GitHub repo and Microsoft Teams workspace using personal emails
Progress: All members set up their environments
Next steps: Jeevan downloads dataset and sets up HDFS. Sri Lakshmi starts cleaning. Deepesh installs dependencies.

## Meeting 2
Date: [fill in]
Attendees: [fill in]
Discussion: [fill in]
Progress: [fill in]
Next steps: [fill in]
```

*Keep updating this file after every meeting or discussion. The TA will check it.*

**A5 — Set Up Microsoft Teams (for team communication)**
Teams is free with a personal Microsoft account. Use personal emails — university emails are blocked from creating teams with channels.

1. Go to `https://teams.microsoft.com` and sign in with your personal Microsoft account (e.g. outlook.com or hotmail.com). If you don't have one, create a free account.
2. Make sure you are on Microsoft Teams (free) — not the work/school version.
3. Click **Teams** on the left sidebar → **Join or create a team**
4. Click **Create team → From scratch → Private**
5. Name it: `Spotify Music Analysis - Phase 1`
6. Click **Add members** and invite Sri Lakshmi and Deepesh using their personal Microsoft emails.

**A6 — Set Up Channels Inside the Team**
Add the following standard channels so discussions stay organized:

* `General` (Default channel, use for announcements)
* `task-1-problem-statement` (Jeevan's notes and decisions)
* `task-2-data-sources` (Sri Lakshmi's updates)
* `task-3-hdfs` (Jeevan's HDFS progress and screenshots)
* `task-4-cleaning` (Sri Lakshmi's cleaning updates and errors)
* `task-5-eda` (Deepesh's EDA updates and chart previews)
* `file-handoffs` (Use this ONLY to share files between teammates)

**A7 — Rules for Using Teams**

* Every time you finish a task, post a message in the relevant channel saying what you did.
* Every time you hand off a file, post it in `#file-handoffs` with a clear message like `"spotify_cleaned.csv ready for Deepesh"`.
* Every meeting or discussion, paste a short summary into `General` — this serves as your Meetings Log.
* If you hit an error, paste the error message in the relevant channel so teammates can help.

---

### SECTION B — SRI LAKSHMI AND DEEPESH: CLONE THE REPO (Each person does this on their own machine)

**B1 — Install Git**
If you don't have Git installed:

* **Windows:** Download from `https://git-scm.com/download/win` and install
* **Mac:** Open Terminal and run `git --version` — it will prompt you to install if missing
* **Linux:** Run `sudo apt install git`

**B2 — Clone the Repository**
Open your terminal and run:

```bash
git clone https://github.com/Seimei95/Spotify_Music_Analysis.git
cd Spotify_Music_Analysis
```

You now have the full project folder on your machine.

**B3 — Set Up Your Identity (one time only)**

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

---

### SECTION C — HOW TO SUBMIT YOUR WORK (All three members follow this every time)

Every time you finish a piece of work (a notebook, a screenshot, a report section), do the following:

**C1 — Put your file in the right folder**

* Notebooks → `notebooks/` folder
* Screenshots → `screenshots/` folder
* Report → `reports/` folder
* Log updates → `logs/` folder

**C2 — Push to GitHub**
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

*(If it asks for a username/password, use your GitHub username and a Personal Access Token).*

**C3 — Pull before you start working (avoid conflicts)**
Every time you sit down to work, first run:

```bash
git pull origin main
```
This makes sure you have everyone else's latest changes before you start.

---

### SECTION D — REPO FILE NAMING RULES (Everyone must follow this)

| File | Person | Where to put it |
| --- | --- | --- |
| `task4_cleaning.ipynb` | Sri Lakshmi | `notebooks/` |
| `task5_eda.ipynb` | Deepesh | `notebooks/` |
| `genre_distribution.png` | Sri Lakshmi | `notebooks/` |
| `eda_plot_1.png` to `eda_plot_4.png` | Deepesh | `notebooks/` (plot 4 = 2x2 boxplot grid) |
| HDFS screenshots | Jeevan | `screenshots/` |
| `work_division.md` | Jeevan | `logs/` |
| `meetings_log.md` | All | `logs/` |
| Final report PDF/DOCX | Jeevan | `reports/` |

⚠️ **Do NOT push `spotify_tracks.csv` or `spotify_cleaned.csv` to GitHub** — they are too large. Keep them only on your local machine and share via Teams or Google Drive.

---

## ✅ CROSS-CHECK WITH INSTRUCTOR REQUIREMENTS

| Requirement | What We're Doing | Status |
| --- | --- | --- |
| ≥ 100,000 rows | Spotify dataset has ~114,000 rows, cleans to ~112k | ✅ |
| N ML problem statements (N=3) | 3 ML tasks defined | ✅ |
| 2N data analysis objectives (2×3=6) | 6 objectives defined | ✅ |
| 2N cleaning operations (2×3=6) | 6 cleaning steps in notebook | ✅ |
| 2N EDA operations (2×3=6) | 6 EDA steps (mix graphical + non-graphical) | ✅ |
| Jupyter Notebook as environment | All code in `.ipynb` files | ✅ |
| HDFS raw dataset (Part A) | Raw CSV uploaded to `/spotify/raw/` | ✅ |
| HDFS cleaned dataset (Part B) | Cleaned CSV uploaded to `/spotify/cleaned/` | ✅ |
| Written report | All tasks documented in report | ✅ |
| Reproducible pipeline | Notebooks run top-to-bottom without errors | ✅ |

---

## ⚡ WORK DIVISION AT A GLANCE

| Person | Tasks | Points |
| --- | --- | --- |
| **Jeevan** | Task 1 (Problem Statement) + Task 3 (HDFS Setup) + Dataset Download | 35 pts |
| **Sri Lakshmi** | Task 2 (Data Sources) + Task 4 (Data Cleaning) | 40 pts |
| **Deepesh** | Task 5 (EDA) | 25 pts |

⚠️ **ORDER MATTERS — Follow this sequence:**

1. Jeevan starts HDFS setup + writes Problem Statement + downloads dataset (simultaneously)
2. Jeevan hands off `spotify_tracks.csv` to Sri Lakshmi
3. Sri Lakshmi runs the cleaning notebook and produces `spotify_cleaned.csv`
4. Sri Lakshmi hands off `spotify_cleaned.csv` to Deepesh AND to Jeevan
5. Deepesh runs EDA notebook
6. Jeevan uploads `spotify_cleaned.csv` to HDFS last

---

## 🕐 TIMELINE (1 Day)

| Time | Jeevan | Sri Lakshmi | Deepesh |
| --- | --- | --- | --- |
| **Hour 0–1** | Write Problem Statement + download dataset from Kaggle | Install Jupyter + dependencies | Install dependencies |
| **Hour 1–3** | Docker + HDFS setup, upload raw CSV, hand off `spotify_tracks.csv` | Wait for CSV, then run cleaning notebook | Wait for cleaned CSV |
| **Hour 3–5** | Wait / help team | Finish cleaning, hand off `spotify_cleaned.csv` | Run EDA notebook |
| **Hour 5–6** | Upload cleaned CSV to HDFS | Compile report section | Compile report section |
| **Hour 6+** | Everyone assembles the final report together | | |

---

## 👤 JEEVAN'S TASKS

### TASK 1 — Problem Statement [20 pts]

*Write all of this in your report. You do NOT need a notebook for this task.*

**Project Title**
"Predicting Track Popularity and Discovering Music Patterns Using the Spotify Tracks Dataset"

**High-Level Problem Statement**
Music streaming platforms serve billions of listeners worldwide and need to understand what makes a track popular in order to power recommendation engines, playlist curation, and artist discovery tools. This project analyzes the Spotify Tracks Dataset — approximately 114,000 tracks with rich audio features and popularity scores provided directly by Spotify — to uncover what audio and metadata features drive track popularity, segment music into natural clusters, and build predictive models.

Stakeholders who benefit from this analysis:

* Streaming platforms (Spotify, Apple Music) optimizing recommendation systems
* Independent artists wanting to understand what makes a track more likely to succeed
* Record labels identifying hit potential before investing in promotion
* Music recommendation system engineers building AI-powered features

**ML Problem Statements (N=3 — one per team member, all go in report)**

* **ML Task 1 — Regression:** Predict a track's popularity score (continuous value 0 to 100) using its audio features such as danceability, energy, loudness, tempo, valence, acousticness, and instrumentalness.
  * Input: Audio feature vector per track
  * Output: Continuous popularity score (float 0–100)
  * Unit of analysis: Per track

* **ML Task 2 — Classification:** Classify each track into one of three popularity tiers — Low (0–33), Medium (34–66), or High (67–100) — using its audio features and genre.
  * Input: Audio features + track_genre
  * Output: 3-class label (low / medium / high)
  * Unit of analysis: Per track

* **ML Task 3 — Clustering / Unsupervised Learning:** Group tracks into natural "mood and vibe" clusters using audio features only, with no labels.
  * Input: Normalized audio feature vector
  * Output: Cluster ID (integer) assigned to each track
  * Unit of analysis: Per track

**Data Analysis Objectives (2N = 6 objectives, all go in report)**

1. Understand the distribution of track popularity across different genres and identify which genres consistently produce high-popularity tracks.
2. Identify which audio features (danceability, energy, loudness, valence, tempo) have the strongest statistical correlation with track popularity.
3. Analyze how audio features such as valence, energy, and tempo vary across different genres.
4. Compare danceability and energy profiles across genres to understand the genre-specific audio fingerprint.
5. Identify the most prolific and highest-popularity artists in the dataset and examine their audio features.
6. Examine the relationship between track duration and popularity to determine whether listener attention span affects streaming performance.

**Input → Output Specification**

* **Input data:** `spotify_tracks.csv`
* **Key fields used:** `track_id`, `artists`, `album_name`, `track_name`, `track_genre`, `popularity`, `duration_ms`, `explicit`, `danceability`, `energy`, `key`, `loudness`, `mode`, `speechiness`, `acousticness`, `instrumentalness`, `liveness`, `valence`, `tempo`, `time_signature`, `duration_minutes`
* **Outputs:**
  * Regression model → predicted popularity score (float)
  * Classification model → popularity tier label (low / medium / high)
  * Clustering model → cluster ID per track (integer)

---

### TASK 3 — HDFS Setup & Ingestion [15 pts]

*This is the most technical part. Follow every step exactly.*

**STEP 1 — Install Docker Desktop**
Download from `https://www.docker.com/products/docker-desktop`, install, and ensure it says "Docker is running".

**STEP 2 — Pull and Start Hadoop Container**
Open your terminal and run:

```bash
docker pull sequenceiq/hadoop-docker:2.7.1
docker run -it -p 50070:50070 -p 9000:9000 --name hadoop_phase1 sequenceiq/hadoop-docker:2.7.1 /etc/bootstrap.sh -bash
```

📸 **TAKE A SCREENSHOT** of the `bash-4.1#` prompt.

**STEP 3 — Create the HDFS Folder Structure**
Inside the Docker container:

```bash
hdfs dfs -mkdir -p /spotify/raw
hdfs dfs -mkdir -p /spotify/cleaned
hdfs dfs -ls /spotify
```

📸 **TAKE A SCREENSHOT** showing `/spotify/raw` and `/spotify/cleaned`.

**STEP 4 — Download the Dataset from Kaggle**
Go to `https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset`, download, and rename the file to `spotify_tracks.csv`.

**STEP 5 — Copy Raw CSV into HDFS**
In a NEW local terminal:

```bash
docker cp /path/to/downloads/spotify_tracks.csv hadoop_phase1:/root/
```

Back in your Docker terminal:

```bash
hdfs dfs -put /root/spotify_tracks.csv /spotify/raw/
hdfs dfs -ls /spotify/raw/
```

📸 **TAKE A SCREENSHOT** showing `spotify_tracks.csv` in HDFS. (Part A Proof)

**STEP 6 — Upload Cleaned CSV (Do this AFTER Sri Lakshmi finishes)**
Once Sri Lakshmi gives you `spotify_cleaned.csv`:

```bash
docker cp /path/to/spotify_cleaned.csv hadoop_phase1:/root/
```

Back in Docker terminal:

```bash
hdfs dfs -put /root/spotify_cleaned.csv /spotify/cleaned/
hdfs dfs -ls /spotify/cleaned/
```

📸 **TAKE A SCREENSHOT** showing `spotify_cleaned.csv` in HDFS. (Part B Proof)

---

## 👤 SRI LAKSHMI'S TASKS

🚨 **READ THIS BEFORE YOU TOUCH ANYTHING**

1. Join the Teams workspace first.
2. Clone the GitHub repo.
3. Do NOT start until Jeevan sends you `spotify_tracks.csv`.
4. Post an update in Teams after EVERY operation you finish.
5. When you finish, post `spotify_cleaned.csv` in the `#file-handoffs` Teams channel.
6. Push your notebook to GitHub when done.
7. If you get an error, paste it in `#task-4-cleaning` immediately. Do not sit on it. Someone will help you fast.

### TASK 2 — Data Sources [15 pts] + TASK 4 — Data Cleaning [25 pts]

**Before You Start:**
Install Jupyter and required libraries: `pip install notebook pandas matplotlib seaborn`
Launch Jupyter: `jupyter notebook`
Create a new notebook called `task4_cleaning.ipynb` next to `spotify_tracks.csv`.

🤖 **STEP 1 — PASTE THIS ENTIRE PROMPT INTO CLAUDE ON YOUR MACHINE**
*(Copy everything in the block below and feed it to Claude)*

```text
You are helping me complete Task 2 (Data Sources) and Task 4 (Data Cleaning) for a university big data course project called Phase 1.

== PROJECT CONTEXT ==
- Topic: Spotify Tracks Dataset — Music Popularity and Audio Feature Analysis
- Dataset file I already have: spotify_tracks.csv
- Team size: 3 people. N=3, so we need exactly 6 cleaning operations total.
- Environment: Jupyter Notebook (local), Python
- Libraries allowed: pandas, matplotlib, seaborn only (no sklearn)

== TASK 2 — DATA SOURCES REPORT SECTION ==
Write a professional report section titled "2. Data Sources" that includes:
- Full citation: PandyaM. (2022). Spotify Tracks Dataset. Kaggle. https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset
- Description of what the dataset contains: ~114,000 Spotify tracks, 125+ genres.
- Key columns: track_id, artists, album_name, track_name, popularity, duration_ms, explicit, danceability, energy, key, loudness, mode, speechiness, acousticness, instrumentalness, liveness, valence, tempo, time_signature, track_genre
- Why this dataset fits our problem
- Confirmation that it exceeds the 100,000 row minimum requirement

== TASK 4 — DATA CLEANING NOTEBOOK ==
Create a complete, runnable Jupyter Notebook called task4_cleaning.ipynb.
For each of the 6 operations below, generate:
1. A markdown cell explaining WHAT we are doing and WHY
2. The full Python code cell (follow the sample style shown below exactly)
3. A markdown cell showing before/after result or what to expect

OPERATION 1 — Load and Inspect the Dataset
- Import pandas, matplotlib.pyplot, seaborn
- Load spotify_tracks.csv using pandas
- Drop the unnamed index column (Unnamed: 0) if it exists — this is a leftover artifact
- Print shape, dtypes, first 5 rows, and df.describe()
Sample style:
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
df = pd.read_csv('spotify_tracks.csv')
if 'Unnamed: 0' in df.columns:
    df = df.drop(columns=['Unnamed: 0'])
    print("Dropped unnamed index column")
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

OPERATION 3 — Duplicate Analysis and Removal
- First analyse duplicates TWO ways before removing anything:
  1. Count duplicates by track_id (same song ID)
  2. Count exact duplicate rows across all columns
- Print both counts and explain the difference in a comment
- Only remove exact duplicate rows (safe — preserves valid multi-genre track entries)
- Print rows before and after removal
Sample style:
dup_id = df.duplicated(subset='track_id').sum()
dup_exact = df.duplicated().sum()
print(f"Duplicate track_id entries: {dup_id}")
print(f"Exact duplicate rows: {dup_exact}")
print("Note: track_id duplicates may represent the same song appearing in multiple genres or playlists.")
print("Therefore, we only remove exact duplicate rows to preserve valid data.")
rows_before = len(df)
df = df.drop_duplicates()
rows_after = len(df)
print(f"\nRows removed: {rows_before - rows_after}")
print(f"Rows remaining: {rows_after}")

OPERATION 4 — Fix Data Types and Convert explicit Column
- Convert duration_ms to duration_minutes by dividing by 60000, round to 2 decimals
- Drop the original duration_ms column after conversion
- Convert explicit column to proper boolean using astype(bool)
- Print the new duration_minutes column and value counts of explicit to confirm
Sample style:
df['duration_minutes'] = (df['duration_ms'] / 60000).round(2)
df = df.drop(columns=['duration_ms'])
df['explicit'] = df['explicit'].astype(bool)
print("New column: duration_minutes")
print(df[['duration_minutes', 'explicit']].head())
print("\nexplicit value counts:", df['explicit'].value_counts())

OPERATION 5 — Flag Zero-Popularity Tracks and Remove Duration Outliers
- Create a new boolean column called is_zero_popularity that is True when popularity == 0
- Print how many tracks have zero popularity and what percentage that is of the total
- Print df['popularity'].describe()
- Also remove tracks where duration_minutes > 15 (these are clearly bad data)
- Print how many rows were removed
Sample style:
df['is_zero_popularity'] = df['popularity'] == 0
zero_count = df['is_zero_popularity'].sum()
total = len(df)
print(f"Zero-popularity tracks: {zero_count} ({100*zero_count/total:.1f}% of dataset)")
print(df['popularity'].describe())
rows_before = len(df)
df = df[df['duration_minutes'] <= 15]
print(f"\nDuration outliers removed: {rows_before - len(df)}")
print(f"Rows remaining: {len(df)}")

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
print(f"Dataset shape after cleaning: {df.shape}")
print(f"The cleaned dataset contains {df.shape[0]:,} rows and {df.shape[1]} columns, suitable for large-scale analysis.")

== IMPORTANT RULES ==
- Every single cell must run without any errors
- Use clear markdown headers between each section
- The notebook must be fully self-contained
- Match the sample style exactly — same variable names, same print messages, same file names
```

📋 **STEP 2 — SAMPLE REFERENCE CODE FOR TASK 4**
*(Use this to verify Claude's output)*

```python
# OPERATION 1
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv('spotify_tracks.csv')
if 'Unnamed: 0' in df.columns:
    df = df.drop(columns=['Unnamed: 0'])
    print("Dropped unnamed index column")

print("Shape:", df.shape)
print("\nData Types:")
print(df.dtypes)
print("\nFirst 5 rows:")
df.head()

# OPERATION 2
print("Missing values per column:")
print(df.isnull().sum())
rows_before = len(df)
df = df.dropna(subset=['artists', 'track_name', 'track_genre'])
rows_after = len(df)
print(f"\nRows removed: {rows_before - rows_after}")
print(f"Rows remaining: {rows_after}")

# OPERATION 3
dup_id = df.duplicated(subset='track_id').sum()
dup_exact = df.duplicated().sum()
print(f"Duplicate track_id entries: {dup_id}")
print(f"Exact duplicate rows: {dup_exact}")
print("Note: track_id duplicates may represent the same song appearing in multiple genres or playlists.")
print("Therefore, we only remove exact duplicate rows to preserve valid data.")
rows_before = len(df)
df = df.drop_duplicates()
rows_after = len(df)
print(f"\nRows removed: {rows_before - rows_after}")
print(f"Rows remaining: {rows_after}")

# OPERATION 4
df['duration_minutes'] = (df['duration_ms'] / 60000).round(2)
df = df.drop(columns=['duration_ms'])
df['explicit'] = df['explicit'].astype(bool)
print("New column: duration_minutes")
print(df[['duration_minutes', 'explicit']].head())
print("\nexplicit value counts:", df['explicit'].value_counts())

# OPERATION 5
df['is_zero_popularity'] = df['popularity'] == 0
zero_count = df['is_zero_popularity'].sum()
total = len(df)
print(f"Zero-popularity tracks: {zero_count} ({100*zero_count/total:.1f}% of dataset)")
print(df['popularity'].describe())
rows_before = len(df)
df = df[df['duration_minutes'] <= 15]
print(f"\nDuration outliers removed: {rows_before - len(df)}")
print(f"Rows remaining: {len(df)}")

# OPERATION 6
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

# FINAL STEP
df.to_csv('spotify_cleaned.csv', index=False)
print(f"Cleaned dataset saved as spotify_cleaned.csv")
print(f"Dataset shape after cleaning: {df.shape}")
print(f"The cleaned dataset contains {df.shape[0]:,} rows and {df.shape[1]} columns, suitable for large-scale analysis.")
```

📤 **Hand Off:** Send `spotify_cleaned.csv` to Deepesh and Jeevan via **Teams `#file-handoffs`** — do not send via WhatsApp or email so there is a clear record.
📸 **Screenshots Required:** Screenshot every code block + output and put them in `screenshots/`.

---

## 👤 DEEPESH'S TASKS

🚨 **READ THIS BEFORE YOU TOUCH ANYTHING**

1. Join the Teams workspace first.
2. Clone the GitHub repo.
3. Do NOT start until Sri Lakshmi posts `spotify_cleaned.csv`.
4. Post an update in Teams after EVERY operation you finish.
5. When you finish, post all 4 chart images + your notebook in Teams.
6. Push your notebook to GitHub when done.
7. If you get an error, paste it in `#task-5-eda` immediately. Do not sit on it. Someone will help you fast.

### TASK 5 — Exploratory Data Analysis [25 pts]

**Before You Start:**
Install dependencies: `pip install notebook pandas matplotlib seaborn numpy`
Launch Jupyter: `jupyter notebook`
Create a new notebook called `task5_eda.ipynb` next to `spotify_cleaned.csv`.

🤖 **STEP 1 — PASTE THIS ENTIRE PROMPT INTO CLAUDE ON YOUR MACHINE**

```text
You are helping me complete Task 5 (Exploratory Data Analysis) for a university big data course project called Phase 1.

== PROJECT CONTEXT ==
- Topic: Spotify Tracks Dataset — Music Popularity and Audio Feature Analysis
- My input file: spotify_cleaned.csv
- Team size: 3 people. N=3, so we need exactly 6 EDA operations total.
- Environment: Jupyter Notebook (local), Python
- Libraries allowed: pandas, matplotlib, seaborn, numpy only (no sklearn)

== YOUR JOB ==
Create a complete, runnable Jupyter Notebook called task5_eda.ipynb.
For each of the 6 EDA operations below, generate:
1. A markdown cell explaining what this analysis is, what it reveals, and why it matters
2. The full Python code cell
3. A markdown interpretation cell with guiding questions to fill in after running

EDA OPERATION 1 — Summary Statistics (Non-graphical)
- Import libraries and load spotify_cleaned.csv
- Run df.describe().round(2)
- Compute skewness and kurtosis for: popularity, danceability, energy, tempo, duration_minutes

EDA OPERATION 2 — Missingness and Zero-Popularity Analysis (Non-graphical)
- Show remaining null counts per column
- Calculate percentage of tracks where is_zero_popularity == True
- Compute mean popularity for zero vs non-zero tracks using groupby

EDA OPERATION 3 — Popularity Distribution (Graphical)
- Histogram of popularity with bins=50 and KDE overlay, mean line (red), median line (orange)
- Save as eda_plot_1.png

EDA OPERATION 4 — Clustered Correlation Heatmap of Audio Features (Graphical)
- Compute correlation matrix for 8 audio features: danceability, energy, loudness, speechiness, acousticness, instrumentalness, valence, tempo
- Plot using sns.clustermap (use annot=True, cmap='coolwarm', figsize=(8,8))
- Save as eda_plot_2.png

EDA OPERATION 5 — Top Genres by Average Popularity (Graphical)
- Mean popularity per track_genre, top 15, horizontal bar chart, save as eda_plot_3.png

EDA OPERATION 6 — Audio Feature Distribution by Popularity Group (Graphical)
- Create a popularity_group column using pd.cut with bins=[0,30,70,100], include_lowest=True, and labels=['Low','Medium','High']
- For each of these 4 features: danceability, energy, valence, acousticness — plot a boxplot showing distribution across the 3 popularity groups
- Save all 4 boxplots in a single 2x2 figure as eda_plot_4.png

FINAL SUMMARY CELL
- Add a final markdown cell titled 'EDA Summary and Implications for Phase 2'
- Include 6 bullet points, one per operation
```

📋 **STEP 2 — SAMPLE REFERENCE CODE FOR TASK 5**
*(Use this to verify Claude's output)*

```python
# EDA OPERATION 1
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

# EDA OPERATION 2
print("=== Remaining Null Values ===")
print(df.isnull().sum())

zero_pct = 100 * df['is_zero_popularity'].sum() / len(df)
print(f"\nPercentage of zero-popularity tracks: {zero_pct:.1f}%")

print("\n=== Mean Popularity: Zero vs Non-Zero ===")
print(df.groupby('is_zero_popularity')['popularity'].mean())

# EDA OPERATION 3
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

# EDA OPERATION 4
audio_features = ['danceability', 'energy', 'loudness', 'speechiness',
                  'acousticness', 'instrumentalness', 'valence', 'tempo']
corr = df[audio_features].corr()
clustermap = sns.clustermap(corr, annot=True, cmap='coolwarm', figsize=(8, 8))
clustermap.savefig('eda_plot_2.png')
plt.show()

# EDA OPERATION 5
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

# EDA OPERATION 6
# include_lowest=True ensures tracks with popularity=0 are included in 'Low' group
df['popularity_group'] = pd.cut(
    df['popularity'],
    bins=[0, 30, 70, 100],
    labels=['Low', 'Medium', 'High'],
    include_lowest=True
)

features = ['danceability', 'energy', 'valence', 'acousticness']
fig, axes = plt.subplots(2, 2, figsize=(12, 10))
axes = axes.flatten()

for i, feature in enumerate(features):
    sns.boxplot(x='popularity_group', y=feature, data=df, ax=axes[i],
                hue='popularity_group', palette='Blues', legend=False, orient='v')
    axes[i].set_title(f'{feature.capitalize()} by Popularity Group')
    axes[i].set_xlabel('Popularity Group')
    axes[i].set_ylabel(feature.capitalize())

plt.suptitle('Audio Feature Distribution by Popularity Group', fontsize=14, y=1.02)
plt.tight_layout()
plt.savefig('eda_plot_4.png')
plt.show()
```

📤 **Hand Off:** Send the following to Jeevan via **Teams `#file-handoffs`** — do not send via WhatsApp or email so there is a clear record:
- `task5_eda.ipynb` — the full EDA notebook
- `eda_plot_1.png`, `eda_plot_2.png`, `eda_plot_3.png`, `eda_plot_4.png` — the four saved chart images
- The **"EDA Summary and Implications for Phase 2"** markdown cell content → copy the text and paste it directly into the team report

📸 **Screenshots Required:** Screenshot every code block + output and put them in `screenshots/`.

---

## 📄 FINAL REPORT STRUCTURE

Assemble the final PDF report exactly like this:

1. **Problem Statement**
   * Project title
   * High-level problem statement + stakeholders
   * 3 ML problem statements (one per team member)
   * 6 data analysis objectives
   * Input → Output specification

2. **Data Sources**
   * Dataset citation and link
   * Dataset description (columns, size, spanning 125+ genres across multiple decades)
   * Justification for dataset choice

3. **Hadoop / HDFS**
   * HDFS commands used
   * Screenshots: Hadoop running, `/spotify/raw/`, `/spotify/cleaned/`

4. **Data Cleaning**
   * Paste from `task4_cleaning.ipynb` (all 6 operations with markdown explanations and screenshots)

5. **Exploratory Data Analysis**
   * Paste from `task5_eda.ipynb` (all 6 operations with interpretations and the 4 saved plot images)

---

## 📌 IMPORTANT REMINDERS

* **Deadline:** March 14, 2026 (Saturday) 11:59 PM EST. Late penalty is 10% per day. No submissions accepted after 3 days late.
* **Submission Format:** A single `.zip` file containing:
  1. `Report.pdf` — written manually in Word/Google Docs and exported to PDF. Must include screenshots of every code cell + output for Tasks 4 & 5, plus HDFS screenshots for Task 3. Do NOT use AI or code to generate the PDF.
  2. `task4_cleaning.ipynb`
  3. `task5_eda.ipynb`
* **Zip file name format:** `ubid1_ubid2_ubid3_phase_1.zip`
* **⚠️ Phase Lock:** After Phase 1 submission you cannot change your dataset or problem statement. Phase 2 builds directly on this. Make sure everyone agrees on the dataset and ML tasks before submitting.
* **Raw data must stay in HDFS** even after uploading the cleaned version. Do not delete it.
* **Jupyter Notebooks** are required — do not submit plain .py files for Tasks 4 and 5.
* **GitHub repo** must be shared with your TA before submission. Commit all notebooks and screenshots. **Do NOT commit CSV files** — they are too large for GitHub.
* **Work Division file:** Must be signed by all 3 members.
* **Meetings Log:** Keep a short log of when you met and what was decided. The TA will check it.