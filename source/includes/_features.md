# Features

This is all the AI features that are available.

enum(ImageFeatures) | enum(TextFeatures) | enum(TextFeatures)
----------- | -----------| -----------
LabelsDetection | EntitiesDetection | Transcription
FacesDetection | SentimentAnalysis |

This is the features that each image processing service implements

Services |  Labels Detection | Faces Detection
-----------|----------- | -----------
Google    | X | X
AWS       | X | X
Clarifai  | X | X


This is the features that each text processing service implements

Services |  Entities Detection | Sentiment Analysis
-----------|----------- | -----------
Aylien    | X | X
IBM | X | X
ParallelDots | X | X
Google | X | X

This is the features that each speech processing service implements

Services |  Transcription
-----------|-----------
IBM | X
Google | X
