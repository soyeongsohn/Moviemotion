# Moviemotion
## Diary Emotion based Movie Recommendation System
### System Architecture
![image](https://github.com/soyeongsohn/Moviemotion/assets/60024018/9d0a7c20-6705-4702-8986-69572df5bcef)
- When user writes a diary in the app, the pre-trained model returns the emotion vectors of the diary from the server
- Return recommended movies and emotion probabilities by calculating cosine similarities between the emotion vector of diary and emotion vectors of movies

### Model Architecture
![image](https://github.com/soyeongsohn/Moviemotion/assets/60024018/e1cc9545-b73c-4820-bdf3-25bba02477a9)
- stack bi-LSTM layer on the top of ELECTRA
- Split sentences by using [KSS (Korean Sentence Splitter)](https://github.com/likejazz/korean-sentence-splitter) and add \<SEP> token between them
- Concatenate the embeddings from \<SEP> tokens of the first and the last sentences and put it in bi-LSTM layer
- Trained the model with the loss which is the sum of the loss from \<CLS> token and the losses from \<SEP> tokens of first and last sentences

### Train
- Added Cosine Annealing Scheduler to solve local minimum problem
- Tried to use Ray to find optimal hyperparameter, but could not get better result

### Result
![image](https://github.com/soyeongsohn/Moviemotion/assets/60024018/4c64d671-9d64-4782-98b4-275bfb88a71f)
- 8% improvement in total

### Role
- Model Design and Implementation
- Implemented ELECTRA + bi-LSTM architecture and add cosine annealing scheduler

### Dataset
[KOTE (Korean Online That-gul Emotions)](https://github.com/searle-j/KOTE)
