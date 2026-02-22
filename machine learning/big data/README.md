# Pumpkinmeter: Scalable Movie Recommendations with Apache Spark
## 🎃 Project Overview
Pumpkinmeter is a sophisticated movie recommendation engine built for "Ripe Pumpkins," a startup specializing in movie review aggregation. Utilizing the MovieLens 27M dataset, this project implements a collaborative filtering model to deliver personalized, high-quality movie suggestions to millions of users.

The core of the system is built on Apache Spark, leveraging its distributed computing power to handle massive datasets and frequent model updates in real-time.

## 🔴 The Challenge: Scale & Latency
- Massive Data: Processing over 27 million ratings and 1.1 million tags across 58,000 movies.
- Infrastructure Constraints: Initial training phases faced significant latency and "Disk Full" errors due to Spark's intensive write operations during model training.
- Cold Start & Quality Control: Ensuring recommendations were not skewed by movies with very few ratings (data noise).

## 🛠️ Technical Implementation
### 1. Distributed Machine Learning (Spark MLlib)
- Implemented the Alternating Least Squares (ALS) algorithm for Collaborative Filtering.
- Designed a distributed pipeline to handle frequent model retraining as new user preferences are ingested.

### 2. Infrastructure & Cloud Optimization
- Compute: Upgraded environment to AWS t2.large instances to provide the necessary CPU and RAM for matrix factorization.
- Storage: Scaled disk volume to 300 GiB to accommodate Spark’s shuffle files and RDD persistence.
- Code Optimization: Minimized execution paths and skipped redundant transformations to reduce computational overhead.

### 3. Data Engineering & Filtering
- Developed a tiered filtering system to increase recommendation reliability.
- Scenario A: Filtered for movies with ≥25 ratings.
- Scenario B: Stricter filter for movies with ≥100 ratings to surface highly-vetted "Masterpiece" content.

## 🚀 Results & Impact
The system successfully generated personalized "Top 5" lists for diverse user profiles, identifying high-affinity content such as Planet Earth II and Band of Brothers with high predictive accuracy.
- Scalability: The architecture is now robust enough to handle increasing user data without performance degradation.
- Performance: After infrastructure tuning, the model successfully processed millions of rows in ~300–600 seconds.
- Personalization: The model demonstrated a strong ability to distinguish between different user tastes (e.g., preference for documentaries vs. intense dramas).

## 🛠️ Tech Stack
- Engine: Apache Spark (PySpark)
-Library: Spark MLlib (ALS Algorithm)
- Cloud: AWS (EC2, Elastic Block Store)
- Dataset: MovieLens 27M (GroupLens Research)