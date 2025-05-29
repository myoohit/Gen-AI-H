# 📘 Kaggle Dataset Handling Guide

## 📤 1) Upload Your Own Dataset (e.g., PDF) to Kaggle

To upload a custom dataset like a PDF:

1. Go to [Kaggle Datasets](https://www.kaggle.com/datasets).
2. Click on the **"Create Dataset"** button (top-right).
3. Fill in the **title**, **subtitle**, and **description**.
4. Drag and drop your **PDF or other files** into the upload box, or click to browse files.
5. Set **visibility** to Public or Private as needed.
6. Click **"Create"** to upload and publish the dataset.

> ⚠️ Once uploaded, use the dataset's slug or URL to access it from a Kaggle notebook:
> 
> ```python
> !kaggle datasets download -d your-username/dataset-name
> ```

---

## 📚 2) Use Built-in Word2Vec Dataset from Kaggle Menu

1. In your Kaggle notebook, click on the **folder icon 📁** on the left sidebar.
2. Click on **"Add data"** (plus icon ➕).
3. In the popup:
   - Use the search bar to search for **"Word2Vec"**.
   - For example, search for `GoogleNews-vectors-negative300` or similar.
4. Click **"Add"** next to the dataset you want.

This will mount the dataset at a path like:

```python
/input/googlenews-vectors-negative300/
```

```python
from gensim.models import KeyedVectors
word_vectors = KeyedVectors.load_word2vec_format('/kaggle/input/googlenews-vectors-negative300/GoogleNews-vectors-negative300.bin.gz', binary=True)
```

## 📦 Using `gdown` with Google Drive File ID

To download files directly from Google Drive in a Kaggle notebook using `gdown`:

### 🔗 Step-by-step:

1. Copy the **Google Drive share link**, e.g.:

```
https://drive.google.com/file/d/1HiegCS_Mqc4QUSXBotGxDATNaY-Ihqhv/view?usp=sharing
```

2. Extract the **file ID** from the URL. It’s the part between `/d/` and `/view`:

```python
File ID = 1HiegCS_Mqc4QUSXBotGxDATNaY-Ihqhv
```


3. Use `gdown` with the `--id` flag in a notebook code cell:
```python
!gdown --id 1HiegCS_Mqc4QUSXBotGxDATNaY-Ihqhv
```
