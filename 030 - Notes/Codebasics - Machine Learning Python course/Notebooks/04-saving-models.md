# Pickle

## Save Model to a File

```python
import pickle
with open('model_pickle','wb') as file:
    pickle.dump(model,file)
```

## Load Model from a File

```python
with open('model_pickle','rb') as file:
    mp = pickle.load(file)
```

# Joblib

```python
from sklearn.externals import joblib
joblib.dump(model, 'model_joblib')
mj = joblib.load('model_joblib')
```
