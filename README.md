# Installation

```
    git clone https://github.com/marlesson/recsys_autoencoders.git
```

 # Data Prepartion
 ```
  mlflow run . -e data_preparation -P min_interactions=5 -P test_size=0.2
 ```
 # Deep AutoEncoder for Collaborative Filtering
 
 ```
    mlflow run . \
          -P activation=selu \
          -P batch=64 \
          -P dropout=0.8 \
          -P epochs=50 \
          -P layers='[512,256,512]' \
          -P lr=0.0001 \
          -P name=auto_enc \
          -P reg=0.01
 ```
 # recommend games for the user
 
 ```
  mlflow run . -e recommender \
          -P name='auto_enc' \
          -P model_path='mlruns/0/<UID>/artifacts/auto_enc' \
          -P topn=10 \
          -P view=0 \
          -P user_id=25
  ```
