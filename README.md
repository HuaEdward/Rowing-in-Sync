# Rowing-in-Sync
A Data-Driven Model to Uncover Synchronization Gaps in Rowing Team Performance

## Abstract:

Synchronization is crucial in rowing, where team success hinges on seamless coordination. This study presents a data-driven model to evaluate rower synchronization by identifying motion inconsistencies. Joint coordinates are extracted from video footage using Mediapipe, and a supervised learning classifier generates motion curves by recognizing labeled rowing states. 

Pairwise similarity between these curves is measured using a composite metric, combining Mean Squared Error, Pearson Correlation, and Area Difference. The k-lowest similarity scores highlight the rower most out of sync, ensuring robust and focused analysis.

This framework offers a clear, quantitative method to uncover synchronization gaps, empowering teams to enhance performance through data-driven insights.

## Rowing motion curve generation: (Rowing_Curve_Generation.ipynb)


The model begins by extracting 3D pose landmarks for each frame in a video using MediaPipe's Pose solution, which detects 33 key body points (x,y,z). These landmarks are normalized for translation and scale, transforming them into embeddings that represent the geometric relationships between key points using pairwise distances. These embeddings are then classified using a k-Nearest Neighbor (k-NN) system, which compares the embeddings against pre-labeled samples for the "Catch" and "Finish" positions. The classification scores for each frame are calculated as confidence values, representing the frame's proximity to either position. These values are smoothed using an Exponential Moving Average (EMA) filter to reduce noise and improve temporal coherence, ultimately constructing a motion curve that visually represents the stroke dynamics across the rowing cycle. This pipeline integrates data preprocessing, classification, and smoothing seamlessly to analyze synchronized rowing strokes effectively.

<img width="468" alt="image" src="https://github.com/user-attachments/assets/0c26cc99-9fa0-46f9-a893-127b5fe81201" />


<img width="463" alt="image" src="https://github.com/user-attachments/assets/5f2144f8-5016-449b-affd-cb6180823751" />
