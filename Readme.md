# 🎵 Spotify Music Analysis — Phase 2 Complete Team Plan
**Course Project | Big Data Pipeline | PySpark + Spark MLlib**
**Dataset:** Spotify Cleaned Dataset from Phase 1 HDFS (`/spotify/cleaned/spotify_cleaned.csv`)
**Team Size:** 3 people | N = 3
**Submission Deadline:** Check UBLearns for exact date/time | Submit via UBLearns

---

## 📌 QUICK NAVIGATION

[✅ Instructor Requirements Checklist](#-cross-check-with-instructor-requirements)
[⚡ Work Division at a Glance](#-work-division-at-a-glance)
[🕐 Timeline](#-timeline)
[🛠️ Environment Setup — All Members](#️-environment-setup--all-members-do-this-first)
[👤 Jeevan's Tasks — Spark Setup + Regression + Hyperparameter Tuning + Report Assembly](#-jeevans-tasks)
[👤 Deepesh's Tasks — Clustering + All 6 Data Analysis Objectives](#-deepeshs-tasks)
[👤 Sri Lakshmi's Tasks — Classification + Report Section](#-sri-lakshmis-tasks)
[📄 Final Report Structure](#-final-report-structure)
[📌 Important Reminders](#-important-reminders)

---

## ✅ CROSS-CHECK WITH INSTRUCTOR REQUIREMENTS

| Requirement | What We're Doing | Status |
| --- | --- | --- |
| N ML algorithms (N=3) | Regression (Jeevan) + Classification (Sri Lakshmi) + Clustering (Deepesh) | ✅ |
| Load data from HDFS cleaned path | All notebooks read from `hdfs://localhost:9000/spotify/cleaned/spotify_cleaned.csv` | ✅ |
| PySpark / Spark MLlib only | No sklearn — only `pyspark.ml` APIs | ✅ |
| Model Training + Evaluation with appropriate metrics | RMSE for regression, F1 + Accuracy for classification, Silhouette for clustering | ✅ |
| Hyperparameter Tuning (≥ 1 algorithm) | CrossValidator + ParamGrid on Regression model (Jeevan) | ✅ |
| Explanation + Analysis for each algorithm | Justification, metrics, visualizations, insights in each notebook | ✅ |
| 2N Data Analysis Objectives (2×3 = 6) | All 6 Phase 1 objectives addressed in Spark (Deepesh) | ✅ |
| Jupyter Notebook (PySpark) | All code in `.ipynb` files with PySpark kernel | ✅ |
| Notebook runs end-to-end without errors | Every notebook must be tested top-to-bottom before submission | ✅ |
| Reproducible on a different machine | No hardcoded local paths — HDFS path only | ✅ |
| Personal statement with signature | All 3 members include signed personal statement in report | ✅ |
| 5-minute video presentation | All members recorded + submitted with zip | ✅ |
| In-person Demo Day (CSE 587 Graduate) | All members present on Demo Day Week 15 | ✅ |

---

## ⚡ WORK DIVISION AT A GLANCE

| Person | Tasks | Points |
| --- | --- | --- |
| **Jeevan** | Spark Environment Setup + ML Task 1 (Regression) + Hyperparameter Tuning + Final Report Assembly | ~40 pts ML + coordination |
| **Deepesh** | ML Task 3 (Clustering) + All 6 Data Analysis Objectives | ~10 pts ML + 30 pts objectives |
| **Sri Lakshmi** | ML Task 2 (Classification) + Report section for Classification | ~10 pts ML + her report section |

> All three contribute equally to the 20 pt Presentation / Demo.

⚠️ **ORDER MATTERS — Follow this sequence:**

1. All three members set up PySpark environment independently (parallel)
2. Jeevan confirms HDFS is running and posts the verified path in Teams
3. Sri Lakshmi runs Classification notebook using HDFS path
4. Deepesh runs Clustering notebook + Data Analysis Objectives notebook using HDFS path
5. Jeevan runs Regression + Hyperparameter Tuning notebook
6. Each person writes their own report section
7. Jeevan assembles all sections into the final report
8. All three record the 5-minute video together

---

## 🕐 TIMELINE

| Phase | Jeevan | Deepesh | Sri Lakshmi |
| --- | --- | --- | --- |
| **Day 1 — Setup** | Start Hadoop container, confirm HDFS path works, install PySpark | Install PySpark, confirm connection to HDFS | Install PySpark, confirm connection to HDFS |
| **Day 2 — ML Notebooks** | Write Regression notebook + Hyperparameter Tuning | Write Clustering notebook | Write Classification notebook |
| **Day 3 — Analysis** | Test notebook end-to-end, fix errors | Write all 6 Data Analysis Objective analyses in Spark | Test notebook end-to-end, write report section |
| **Day 4 — Report** | Assemble full report from all sections | Finalize analysis notebook + write report section | Submit report section to Jeevan |
| **Day 5 — Final** | Final checks, zip submission, record video together | Record video + review submission | Record video + review submission |

---

## 🛠️ ENVIRONMENT SETUP — ALL MEMBERS (Do this first)

### Install PySpark

```bash
pip install pyspark findspark
```

### Start Your Phase 1 Hadoop Container

If you stopped it after Phase 1:

```bash
docker start hadoop_phase1
docker exec -it hadoop_phase1 /bin/bash
```

Confirm HDFS is running inside the container:

```bash
hdfs dfs -ls /spotify/cleaned/
```

You should see `spotify_cleaned.csv` listed. If not, contact Jeevan — the file may need to be re-uploaded from Phase 1.

### Connect PySpark to HDFS

At the top of every notebook, use this exact SparkSession setup:

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("SpotifyPhase2") \
    .config("spark.hadoop.fs.defaultFS", "hdfs://localhost:9000") \
    .getOrCreate()

df = spark.read.csv(
    "hdfs://localhost:9000/spotify/cleaned/spotify_cleaned.csv",
    header=True,
    inferSchema=True
)
df.printSchema()
print(f"Total rows: {df.count()}")
```

⚠️ **Do NOT load from a local CSV file.** The notebook must load from HDFS to satisfy the course requirement.

### Exact Columns in `spotify_cleaned.csv` (21 columns, 113,400 rows)

These are confirmed from the Phase 1 cleaning notebook output:

```
track_id          — string
artists           — string
album_name        — string
track_name        — string
popularity        — integer (0–100)
explicit          — boolean (True/False)
danceability      — float (0.0–1.0)
energy            — float (0.0–1.0)
key               — integer (0–11)
loudness          — float (negative, in dB)
mode              — integer (0 or 1)
speechiness       — float (0.0–1.0)
acousticness      — float (0.0–1.0)
instrumentalness  — float (0.0–1.0)
liveness          — float (0.0–1.0)
valence           — float (0.0–1.0)
tempo             — float (BPM)
time_signature    — integer
track_genre       — string (114 unique genres, already lowercase)
duration_minutes  — float (replaced duration_ms from Phase 1)
is_zero_popularity — boolean (True when popularity == 0, ~14% of data)
```

> **Important for PySpark:**
> - `explicit` and `is_zero_popularity` load as **BooleanType** with `inferSchema=True`
> - VectorAssembler **cannot handle BooleanType** — cast to IntegerType first if using as a feature
> - `popularity_group` (Low/Medium/High) does **NOT** exist in the CSV — you must create it in your notebook
> - `duration_ms` does **NOT** exist — use `duration_minutes` instead

---

## 👤 JEEVAN'S TASKS

### TASK: Spark Environment Lead + ML Task 1 — Regression [Hardest]

You are responsible for:
1. Confirming HDFS is running and sharing the verified path with the team
2. Writing the Regression ML notebook with Hyperparameter Tuning
3. Assembling the final report

---

### Notebook: `task1_regression.ipynb`

🤖 **PASTE THIS PROMPT INTO CLAUDE TO GENERATE YOUR NOTEBOOK**

```
You are helping me complete ML Task 1 (Regression) for a university big data course — Phase 2.

== STRICT CONSTRAINTS — READ BEFORE GENERATING ANYTHING ==
- Environment: Jupyter Notebook, PySpark (pyspark.ml only)
- No pandas ML, no sklearn, no numpy ML — only pyspark.ml APIs
- Data is loaded from HDFS: hdfs://localhost:9000/spotify/cleaned/spotify_cleaned.csv
- The notebook must run end-to-end without errors
- Use inferSchema=True when loading

== EXACT COLUMN INFORMATION — DO NOT DEVIATE ==
The CSV has exactly 21 columns and 113,400 rows after Phase 1 cleaning:
  track_id (string), artists (string), album_name (string), track_name (string),
  popularity (integer, 0-100), explicit (boolean — True/False),
  danceability (float), energy (float), key (integer),
  loudness (float, negative dB), mode (integer 0 or 1),
  speechiness (float), acousticness (float), instrumentalness (float),
  liveness (float), valence (float), tempo (float),
  time_signature (integer), track_genre (string),
  duration_minutes (float — replaces duration_ms which does NOT exist),
  is_zero_popularity (boolean — True when popularity == 0)

== TASK CONTEXT ==
ML Task 1 — Regression:
- Goal: Predict a track's popularity score (continuous, 0–100) from audio features
- Input features: danceability, energy, loudness, speechiness, acousticness,
  instrumentalness, liveness, valence, tempo, duration_minutes
- Target column: popularity (integer/float)
- Unit of analysis: per track

== NOTEBOOK STRUCTURE — Generate exactly these sections ==

SECTION 1 — Setup and Data Loading
- SparkSession with appName="SpotifyRegression" and hdfs://localhost:9000 as defaultFS
- Load CSV from HDFS with header=True, inferSchema=True
- Print schema and total row count
- Drop rows where popularity is null
- Drop the is_zero_popularity column — it is not a model feature

SECTION 2 — Feature Engineering
- Cast explicit to IntegerType using df.withColumn("explicit", df["explicit"].cast("integer"))
  (BooleanType cannot go into VectorAssembler directly)
- Use VectorAssembler to assemble these 10 columns into a single features vector:
  danceability, energy, loudness, speechiness, acousticness,
  instrumentalness, liveness, valence, tempo, duration_minutes
- Do NOT include track_id, artists, album_name, track_name, track_genre, explicit,
  key, mode, time_signature, or is_zero_popularity in the features vector
- Show the first 5 rows of the assembled dataframe with features and popularity columns only

SECTION 3 — Train/Test Split
- Split assembled data into 80% train, 20% test using randomSplit([0.8, 0.2], seed=42)
- Print train and test row counts

SECTION 4 — Model 1: Linear Regression
- Train pyspark.ml.regression.LinearRegression with featuresCol="features", labelCol="popularity"
- Evaluate on test set using pyspark.ml.evaluation.RegressionEvaluator with metricName="rmse"
- Also compute R2 (metricName="r2")
- Print RMSE and R2
- Add a markdown cell explaining what RMSE and R2 mean in this context

SECTION 5 — Model 2: Random Forest Regressor
- Train pyspark.ml.regression.RandomForestRegressor with featuresCol="features",
  labelCol="popularity", numTrees=50, seed=42
- Evaluate on test set — print RMSE and R2
- Extract and print feature importances as a sorted list pairing feature names
  with importance scores (use the 10 feature names from the assembly step)
- Add a markdown cell interpreting which features matter most

SECTION 6 — Hyperparameter Tuning on Random Forest
- Use pyspark.ml.tuning.ParamGridBuilder to define a grid over:
  numTrees: [50, 100]
  maxDepth: [5, 10]
- Use pyspark.ml.tuning.CrossValidator with:
  estimator = RandomForestRegressor(featuresCol="features", labelCol="popularity", seed=42)
  evaluator = RegressionEvaluator(labelCol="popularity", metricName="rmse")
  numFolds = 3
- Fit CrossValidator on training data
- Evaluate best model on test set — print RMSE and R2
- Print the best hyperparameters found
- Add a markdown cell explaining why cross-validation matters and what improved

SECTION 7 — Visualization (matplotlib, collected to driver)
- Collect predictions from best model on test set to pandas:
  .select("popularity", "prediction").toPandas()
- Plot a scatter plot: actual popularity (x-axis) vs predicted popularity (y-axis)
- Add a red diagonal reference line (y=x) to show perfect prediction
- Title: "Actual vs Predicted Popularity (Random Forest Tuned)"
- Save as regression_plot.png

SECTION 8 — Analysis and Conclusion Markdown Cell
Write a markdown cell that addresses:
- Why you chose Linear Regression and Random Forest for this regression task
- How training and hyperparameter tuning were performed
- What the RMSE and R2 values tell you about model effectiveness
- Which audio features were most predictive of popularity and what that implies
- One limitation of this regression approach on this dataset

== OUTPUT FORMAT ==
Generate a complete Jupyter Notebook with alternating markdown cells and code cells
exactly as described above. Every code cell must be syntactically correct PySpark.
Do not add sections not listed above.
```

---

### Final Report Assembly (Jeevan)

After Sri Lakshmi and Deepesh hand you their sections, compile everything into the final PDF report following the structure in the [Final Report Structure](#-final-report-structure) section below.

---

## 👤 DEEPESH'S TASKS

### TASK: ML Task 3 — Clustering + All 6 Data Analysis Objectives [Second Hardest]

You are responsible for:
1. Writing the Clustering ML notebook
2. Writing the Data Analysis Objectives notebook (all 6 objectives from Phase 1 — now executed in Spark)
3. Writing your own report sections for both

---

### Notebook 1: `task3_clustering.ipynb`

🤖 **PASTE THIS PROMPT INTO CLAUDE TO GENERATE YOUR NOTEBOOK**

```
You are helping me complete ML Task 3 (Clustering) for a university big data course — Phase 2.

== STRICT CONSTRAINTS ==
- Environment: Jupyter Notebook, PySpark (pyspark.ml only)
- No pandas ML, no sklearn — only pyspark.ml APIs
- Data loaded from HDFS: hdfs://localhost:9000/spotify/cleaned/spotify_cleaned.csv
- Notebook must run end-to-end without errors
- Use inferSchema=True

== EXACT COLUMN INFORMATION — DO NOT DEVIATE ==
The CSV has exactly 21 columns and 113,400 rows:
  track_id (string), artists (string), album_name (string), track_name (string),
  popularity (integer), explicit (boolean — True/False),
  danceability (float), energy (float), key (integer),
  loudness (float, negative dB), mode (integer),
  speechiness (float), acousticness (float), instrumentalness (float),
  liveness (float), valence (float), tempo (float),
  time_signature (integer), track_genre (string),
  duration_minutes (float), is_zero_popularity (boolean)

Columns that do NOT exist: duration_ms, popularity_group

== TASK CONTEXT ==
ML Task 3 — Clustering:
- Goal: Group tracks into natural "mood and vibe" clusters using audio features only
- Input features: danceability, energy, loudness, speechiness, acousticness,
  instrumentalness, valence, tempo (8 audio features)
- Output: cluster ID per track (integer)
- No labels used — unsupervised learning

== NOTEBOOK STRUCTURE ==

SECTION 1 — Setup and Data Loading
- SparkSession with appName="SpotifyClustering"
- Load from HDFS with header=True, inferSchema=True
- Print schema and total row count
- Drop nulls from all 8 feature columns

SECTION 2 — Feature Assembly and Scaling
- Assemble 8 columns (danceability, energy, loudness, speechiness, acousticness,
  instrumentalness, valence, tempo) using VectorAssembler into "features"
- Apply pyspark.ml.feature.StandardScaler (withMean=True, withStd=True) on features
  → output column "scaled_features"
- This is required because loudness has a very different scale than the others
  (loudness is in dB, typically negative, while others are 0.0–1.0)

SECTION 3 — Determine Optimal K (Elbow Method)
- Train KMeans (pyspark.ml.clustering.KMeans) with k = 2, 3, 4, 5, 6, 7, 8
  on scaled_features
- For each k, compute the Within Set Sum of Squared Errors (WSSSE) using
  model.summary.trainingCost
- Collect k and WSSSE values to a Python list, then plot WSSSE vs k as a line
  chart using matplotlib
- Save as clustering_elbow.png
- In a markdown cell, identify and justify your chosen k value based on the elbow plot

SECTION 4 — Final KMeans Model
- Train KMeans with your chosen k (use k=4 if the elbow is not obvious) and seed=42
  on scaled_features
- Add cluster predictions to the dataframe: model.transform(df)
- Print cluster sizes using groupBy("prediction").count().orderBy("prediction").show()

SECTION 5 — Cluster Evaluation
- Compute Silhouette Score using pyspark.ml.evaluation.ClusteringEvaluator
  with featuresCol="scaled_features"
- Print the silhouette score and interpret it in a markdown cell
  (range -1 to 1; closer to 1 means clusters are well separated)

SECTION 6 — Cluster Profiling
- Compute mean values of all 8 audio features per cluster using
  groupBy("prediction").mean(feature names)
- Collect result to pandas and display as a formatted table
- In a markdown cell, describe each cluster's character based on its mean
  feature values (example: "Cluster 2 has high energy and high danceability
  — likely pop/dance tracks")

SECTION 7 — Visualization
- Collect a sample to pandas: .select("prediction", "danceability", "energy", "valence").toPandas()
- Scatter plot: danceability (x-axis) vs energy (y-axis), colored by prediction (cluster ID)
- Use a colormap (e.g., plt.scatter with c=pred_col, cmap='tab10')
- Add a colorbar, title, and axis labels
- Save as clustering_scatter.png

SECTION 8 — Analysis and Conclusion Markdown Cell
Write a markdown cell addressing:
- Why KMeans was chosen for this clustering task
- What the silhouette score says about cluster quality
- What each cluster likely represents in terms of music mood or style
- One limitation of KMeans for this dataset

== OUTPUT FORMAT ==
Complete Jupyter Notebook with alternating markdown and code cells as described.
No extra sections. All PySpark code must be syntactically correct.
```

---

### Notebook 2: `task_data_analysis_objectives.ipynb`

🤖 **PASTE THIS PROMPT INTO CLAUDE TO GENERATE YOUR NOTEBOOK**

```
You are helping me complete the Data Analysis Objectives section for a university
big data course — Phase 2.

== STRICT CONSTRAINTS ==
- Environment: Jupyter Notebook, PySpark + matplotlib + seaborn
- All analysis must be done using PySpark DataFrame operations
  (groupBy, agg, orderBy, filter, etc.)
- Visualizations use matplotlib/seaborn ONLY on data collected to the driver
  via .toPandas() or .collect() AFTER PySpark computation
- Data loaded from HDFS: hdfs://localhost:9000/spotify/cleaned/spotify_cleaned.csv
- Notebook must run end-to-end without errors
- Use inferSchema=True

== EXACT COLUMN INFORMATION — DO NOT DEVIATE ==
The CSV has exactly 21 columns and 113,400 rows:
  track_id (string), artists (string), album_name (string), track_name (string),
  popularity (integer), explicit (boolean — True/False),
  danceability (float), energy (float), key (integer),
  loudness (float, negative dB), mode (integer),
  speechiness (float), acousticness (float), instrumentalness (float),
  liveness (float), valence (float), tempo (float),
  time_signature (integer), track_genre (string, 114 unique genres, already lowercase),
  duration_minutes (float), is_zero_popularity (boolean)

Columns that do NOT exist: duration_ms, popularity_group

== TASK CONTEXT ==
These are the 6 data analysis objectives defined in Phase 1 that must now be
addressed using Spark. For each objective: (a) PySpark analysis code,
(b) a visualization where appropriate, (c) a markdown interpretation cell.

== SIX OBJECTIVES ==

OBJECTIVE 1 — Popularity Distribution Across Genres
- SparkSession setup with appName="SpotifyObjectives" + load from HDFS
- Use groupBy("track_genre").agg(avg("popularity").alias("avg_pop"),
  count("track_id").alias("track_count"))
- Filter to genres with at least 200 tracks to avoid noise
- Sort by avg_pop descending, take top 20, collect to pandas
- Horizontal bar chart, save as obj1_genre_popularity.png
- Markdown interpretation: Which genres consistently produce high-popularity tracks?

OBJECTIVE 2 — Audio Feature Correlation with Popularity
- Select columns: popularity, danceability, energy, loudness, valence, tempo,
  acousticness, instrumentalness, speechiness, duration_minutes
- Use pyspark.ml.stat.Correlation.corr() — first assemble all 10 columns into
  a vector using VectorAssembler, then call Correlation.corr(assembled_df, "features")
- Extract the correlation values for the popularity dimension (first column/row)
  and pair each value with its feature name
- Plot a horizontal bar chart of Pearson correlations with popularity, sorted
  by absolute value, save as obj2_feature_correlation.png
- Markdown interpretation: Which features have the strongest linear relationship
  with popularity?

OBJECTIVE 3 — Audio Feature Variation Across Genres
- First find the top 10 genres by track count:
  groupBy("track_genre").count().orderBy(desc("count")).limit(10).collect()
- Filter the dataframe to only these 10 genres
- For each of these 3 features: valence, energy, tempo —
  use groupBy("track_genre").agg(avg(feature))
- Collect to pandas, plot a grouped bar chart (3 feature bars side by side per genre)
- Save as obj3_genre_audio_features.png
- Markdown: How do these audio features differ across genres?

OBJECTIVE 4 — Danceability and Energy Profiles Across Genres
- Use the same top 10 genres from Objective 3
- groupBy("track_genre").agg(avg("danceability").alias("avg_dance"),
  avg("energy").alias("avg_energy"))
- Collect to pandas, scatter plot: avg_dance (x) vs avg_energy (y),
  with each point labeled by genre name using ax.annotate()
- Save as obj4_dance_energy.png
- Markdown: Do genres cluster into distinct danceability-energy profiles?

OBJECTIVE 5 — Most Prolific and Highest-Popularity Artists
- groupBy("artists").agg(count("track_id").alias("track_count"),
  avg("popularity").alias("avg_popularity"))
- Filter to artists with track_count >= 10
- Two subplots: (a) Top 15 by track_count (horizontal bar); (b) Top 15 by
  avg_popularity among filtered artists (horizontal bar)
- Combine into a single 1x2 subplot figure, save as obj5_artists.png
- Markdown: Are the most prolific artists also the most popular?

OBJECTIVE 6 — Track Duration vs Popularity
- Create duration buckets using a Spark SQL when().otherwise() expression:
    < 2.0 minutes → "< 2 min"
    2.0 to < 3.0 → "2-3 min"
    3.0 to < 4.0 → "3-4 min"
    4.0 to < 5.0 → "4-5 min"
    >= 5.0       → "> 5 min"
- groupBy("duration_bucket").agg(avg("popularity").alias("avg_pop"),
  count("*").alias("track_count"))
- Collect to pandas, order buckets correctly, bar chart of avg_pop per bucket
- Save as obj6_duration_popularity.png
- Markdown: Does track duration affect streaming popularity?

FINAL SUMMARY CELL
- Markdown cell titled "Data Analysis Objectives — Summary of Findings"
- 6 bullet points, one per objective, 2–3 sentences each

== OUTPUT FORMAT ==
Complete Jupyter Notebook. All PySpark code syntactically correct.
All 6 objectives included in order. No extra sections.
```

---

## 👤 SRI LAKSHMI'S TASKS

🚨 **READ THIS BEFORE YOU TOUCH ANYTHING**

1. Do NOT start until Jeevan confirms HDFS is running and posts the verified path.
2. Test your HDFS connection before writing any ML code (see Environment Setup above).
3. Push your notebook to GitHub when done.
4. Send Jeevan your finished report section.

### Notebook: `task2_classification.ipynb`

🤖 **PASTE THIS PROMPT INTO CLAUDE TO GENERATE YOUR NOTEBOOK**

```
You are helping me complete ML Task 2 (Classification) for a university big data
course — Phase 2.

== STRICT CONSTRAINTS ==
- Environment: Jupyter Notebook, PySpark (pyspark.ml only)
- No pandas ML, no sklearn — only pyspark.ml APIs
- Data loaded from HDFS: hdfs://localhost:9000/spotify/cleaned/spotify_cleaned.csv
- Notebook must run end-to-end without errors
- Use inferSchema=True

== EXACT COLUMN INFORMATION — DO NOT DEVIATE ==
The CSV has exactly 21 columns and 113,400 rows:
  track_id (string), artists (string), album_name (string), track_name (string),
  popularity (integer, 0-100), explicit (boolean — True/False),
  danceability (float), energy (float), key (integer),
  loudness (float, negative dB), mode (integer 0 or 1),
  speechiness (float), acousticness (float), instrumentalness (float),
  liveness (float), valence (float), tempo (float),
  time_signature (integer), track_genre (string, 114 unique genres),
  duration_minutes (float), is_zero_popularity (boolean)

Columns that do NOT exist: duration_ms, popularity_group
Note: explicit and is_zero_popularity load as BooleanType with inferSchema=True.
VectorAssembler CANNOT handle BooleanType — cast to integer if you use them as features.

== TASK CONTEXT ==
ML Task 2 — Classification:
- Goal: Classify each track into one of three popularity tiers:
  Low (0–33), Medium (34–66), High (67–100)
- Input features: danceability, energy, loudness, speechiness, acousticness,
  instrumentalness, liveness, valence, tempo, duration_minutes,
  and track_genre (encoded as numeric index via StringIndexer)
- Target: 3-class integer label (0=Low, 1=Medium, 2=High) derived from popularity

== NOTEBOOK STRUCTURE ==

SECTION 1 — Setup and Data Loading
- SparkSession with appName="SpotifyClassification"
- Load from HDFS, print schema and total row count
- Drop rows where popularity is null

SECTION 2 — Create Target Label Column
- Use pyspark.sql.functions.when().otherwise() to create "popularity_label":
    popularity <= 33  → integer 0  (Low)
    popularity <= 66  → integer 1  (Medium)
    popularity > 66   → integer 2  (High)
  Use col("popularity") in the conditions. Cast result to IntegerType.
- Show label distribution: groupBy("popularity_label").count().orderBy("popularity_label").show()
- In a markdown cell, note any class imbalance you observe

SECTION 3 — Encode track_genre and Assemble Features
- Use StringIndexer to encode track_genre → track_genre_index (string → float index)
  inputCol="track_genre", outputCol="track_genre_index"
- Assemble these 11 columns into "features" using VectorAssembler:
  danceability, energy, loudness, speechiness, acousticness,
  instrumentalness, liveness, valence, tempo, duration_minutes, track_genre_index
- Do NOT include explicit, is_zero_popularity, key, mode, time_signature,
  or non-numeric ID/name columns in features
- Show first 5 rows with features and popularity_label columns

SECTION 4 — Train/Test Split
- randomSplit([0.8, 0.2], seed=42)
- Print train and test row counts

SECTION 5 — Model 1: Logistic Regression (Multinomial)
- Train pyspark.ml.classification.LogisticRegression with:
  featuresCol="features", labelCol="popularity_label",
  family="multinomial", maxIter=100
- Evaluate on test set using MulticlassClassificationEvaluator:
  metricName="accuracy" → print accuracy
  metricName="f1"       → print F1 score
- Markdown cell: interpret what accuracy and F1 mean for a 3-class problem

SECTION 6 — Model 2: Random Forest Classifier
- Train pyspark.ml.classification.RandomForestClassifier with:
  featuresCol="features", labelCol="popularity_label", numTrees=50, seed=42
- Evaluate on test set — print accuracy and F1
- Extract and print feature importances sorted descending
  (pair the 11 feature names from Section 3 with importance scores)
- Markdown cell: which features matter most for predicting popularity tier?

SECTION 7 — Confusion Matrix (Collected to Driver)
- Use the better-performing model's predictions
- Collect predictions and true labels to pandas:
  .select("popularity_label", "prediction").toPandas()
- Use pandas to build a 3x3 confusion matrix (groupby or crosstab)
- Plot it as a seaborn heatmap (annot=True, fmt="d")
- Label axes: x-axis "Predicted" with ticks [Low, Medium, High];
              y-axis "Actual" with ticks [Low, Medium, High]
- Save as classification_confusion_matrix.png
- Markdown: Which classes does the model confuse most often?

SECTION 8 — Analysis and Conclusion Markdown Cell
Write a markdown cell addressing:
- Why you chose Logistic Regression and Random Forest for this classification task
- How you handled the multi-class target (3 tiers) and any class imbalance
- What the accuracy and F1 scores say about model effectiveness
- Which features were most predictive of popularity tier
- One limitation of this classification approach

== OUTPUT FORMAT ==
Complete Jupyter Notebook with alternating markdown and code cells as described.
All PySpark code must be syntactically correct. No extra sections.
```

---

## 📄 FINAL REPORT STRUCTURE

Assemble the final PDF report exactly like this. **Do NOT use AI or code to generate the PDF.** Write it manually in Word or Google Docs, export to PDF.

### 1. Introduction / Problem Statement *(from Phase 1 — brief recap)*
- Project title
- Problem statement and stakeholders
- 3 ML tasks (recap from Phase 1)
- 6 analysis objectives (recap from Phase 1)

### 2. Data Sources *(from Phase 1 — brief recap only)*
- Dataset citation
- Cleaned dataset specs: 113,400 rows, 21 columns (list the column names)

### 3. Spark ML — Task 1: Regression *(Jeevan writes)*
- Algorithm justification: why Linear Regression and Random Forest
- Training procedure and hyperparameter tuning description
- Results: RMSE and R2 for each model (pre-tuning vs post-tuning)
- Feature importance table (10 features)
- Insert: `regression_plot.png`
- Analysis: what this tells us about predicting popularity

### 4. Spark ML — Task 2: Classification *(Sri Lakshmi writes)*
- Algorithm justification: why Logistic Regression and Random Forest
- Training procedure and class imbalance notes
- Results: Accuracy and F1 for each model
- Feature importance table (11 features)
- Insert: `classification_confusion_matrix.png`
- Analysis: what this tells us about predicting popularity tier

### 5. Spark ML — Task 3: Clustering *(Deepesh writes)*
- Algorithm justification: why KMeans
- Elbow method and chosen k
- Silhouette score and interpretation
- Cluster profiles (mean feature values per cluster)
- Insert: `clustering_elbow.png`, `clustering_scatter.png`
- Analysis: what each cluster likely represents musically

### 6. Data Analysis Objectives *(Deepesh writes)*
- Objective 1 through 6
- Each: description of analysis, Spark approach, key finding, insert chart
- Final summary of cross-objective insights

### 7. Conclusion
- Summary of all 3 ML results
- Which model performed best and why
- How the findings address the Phase 1 problem statement
- Limitations and potential Phase 3 directions

### 8. Personal Statements *(Required — each member writes their own)*
Each member must include:
- What you personally contributed to Phase 2
- What you learned
- Your signature

> Example format:
> "I, [Name], personally completed [tasks]. I confirm that my submitted work is my own and not generated by AI. Signature: _______________"

---

## 📌 IMPORTANT REMINDERS

* **Submission Format:** A single `.zip` file containing:
  1. `Report.pdf` — written manually, exported to PDF. Must include screenshots of every code block + output for all three notebooks, plus all chart images.
  2. `task1_regression.ipynb`
  3. `task2_classification.ipynb`
  4. `task3_clustering.ipynb`
  5. `task_data_analysis_objectives.ipynb`
  6. Video presentation file (5 minutes, all members speaking)
* **Zip file name format:** `ubid1_ubid2_ubid3_phase_2.zip`
* **Do NOT change your dataset or problem statements** — Phase 2 is locked to Phase 1 definitions.
* **All notebooks must load data from HDFS**, not from a local CSV file.
* **No hardcoded local paths.** The notebook must be runnable on the grader's machine.
* **GitHub repo** must be updated with all Phase 2 notebooks. Do NOT commit CSV files.
* **Every code cell must be screenshot** for the report — run each cell and screenshot the output as you go.
* **Personal statement with signature** is required from all 3 members in the report.
* **It is your responsibility** to verify that nothing you submit is AI-generated output presented as your own analysis. Claude prompts above are starting points — understand every line before submitting.
* **In-person Demo Day (CSE 587):** All three members must be present. Prepare to explain your code and results live.
