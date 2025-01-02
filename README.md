# UDA Final Project
## Joshua Stapleton
## CID: 02301776
## 03/01/2025

This is my own work, which I have completed independently. I provide some high level details here, but the full formal analysis / writeup is given in `UDA_FinalProject_Stapleon.ipynb`.

![Demo GIF](route_demo.gif)

This project aims to identify my primary running routes from raw geospatial trajectories recorded over the past year. The analysis combines techniques in geospatial data processing, dimensionality reduction, and clustering to reveal patterns in my running data. The detailed analysis and writeup is documented in `UDA_FinalProject_Stapleton.ipynb`.

## Problem Statement

The goal is to transform raw geospatial-temporal data into a structured network of running routes. Specifically:
1.	Represent trajectories as graphs/networks, where nodes are derived from dimensionality reduction and edges represent continuity.
2.	Identify and cluster the most frequent routes by measuring and grouping similar trajectories.

This analysis serves as both a personal exploration and a scalable methodology for fitness applications.

## Methods

1. Data Collection:
- Source: Apple Watch’s .gpx files, exported via Apple Health.
- Structure: Tracks (`<trk>`) containing segments (`<trkseg>`) and geospatial points (`<trkpt>`).
- Preprocessing: Dimensionality reduction and geographic filtering narrowed the dataset to routes primarily in Ballito, South Africa where I am based most of the time.

2. Exploratory Data Analysis (EDA):
- Visualization of raw routes on an interactive map (using folium).
- Summary statistics revealed 656 runs, with an average distance of 3.85 km, a maximum of 22.15 km, and a minimum of 0.00045 km.

3. Dimensionality Reduction and Clusteringg:
- Downsampling: Trajectories were reduced to 100 points per route to balance fidelity and computational efficiency.
- t-SNE & KMeans: Routes were embedded into 2D space and clustered. Elbow plots informed the optimal number of clusters.
- Spectral Clustering: Used affinity matrices to identify more cohesive clusters, validated by silhouette scores (0.674) and Davies-Bouldin Index (0.683).

4. Visualization
- Representative routes for each cluster were displayed on maps, highlighting overlap and uniqueness of common running paths. The discovered routes align with my expectations.

## Findings
1.	Route Discovery:
- Successfully identified five primary running routes in Ballito.
-	Routes clustered based on frequency and overlap, with minor inaccuracies (e.g., over-segmentation of a popular 5 km route) under t-SNE.
2.	Algorithmic Insights:
- Spectral Clustering outperformed t-SNE + KMeans in accuracy and efficiency.
- Computation was highly scalable, achieving near-production speeds on an NVIDIA RTX 6000 GPU.

## Limitations
- Some inaccuracies in clustering in t-SNE, likely due to dimensionality reduction artifacts (e.g., t-SNE distortions).
- Geographic outliers required manual filtering to avoid skewing results.

## Applications

The pipeline demonstrates potential for large-scale fitness applications:
- Personalized route discovery for runners.
- Insights into popular routes for urban planning or fitness apps like Strava or Nike Run Club.

## Usage

To reproduce results:
1.	Install dependencies listed in the notebook.
2.	Run all cells in UDA_FinalProject_Stapleton.ipynb.
3.	View interactive maps and visualizations generated during analysis.

This analysis was both a personal exploration and a rigorous application of concepts from the UDA module, showcasing practical use cases for geospatial trajectory analysis. Further optimizations could enhance scalability and precision for broader use cases.