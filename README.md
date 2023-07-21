# NLP: Text generation 💬

<div id="header" align="center">
  <img src="https://media.giphy.com/media/ILGeonVyEZ4EE/giphy.gif" width="250"/>
</div>

---

## ✍️ What is this project about
Don't let Salem confuse you! 
**The main goal is to generate a new article based on user's request and existing articles put in the custom dataset.**

---

## Collecting the dataset
1. At first there was an idea to parse articles from the web-sites with different news. The corresponding code is in this [parsing notebook.](https://github.com/Daryadare/NLP-Text-Generation/blob/main/parsing.ipynb)
2. But since the news needed to be of various topics parsing and post-processing every article wasn't the best solution. So the dataset was manually collected and saved as .csv table sheet. You can observe the process in this [data mining notebook.](https://github.com/Daryadare/NLP-Text-Generation/blob/main/data-mining.ipynb)

---

## Workflow
Let's examine [NLP-proj notebook:](https://github.com/Daryadare/NLP-Text-Generation/blob/main/NLP-proj.ipynb)
1. The articles from our dataset are converted to **Embeddings** using **CLS pooling**. We also add **FAISS index**, so we could use **the nearest neighbour search.** This way we get 10 'nearest' articles to user's request.
2. Then using the pre-trained [model](https://huggingface.co/csebuetnlp/mT5_multilingual_XLSum) from the resource [HuggingFace](https://huggingface.co/) we get a new article that is a summary of 10 chosen in the previous step.
3. To check the accuracy we use such metrics for generative models as [BLEURT](https://github.com/google-research/bleurt) and [Meteor](https://huggingface.co/spaces/evaluate-metric/meteor).

The **final** notebook of this project is [NLP-Text-Generation](https://github.com/Daryadare/NLP-Text-Generation/blob/main/NLP-text-generation.ipynb).
1. It contains all the things listed earlier except for user request, because the aim was to generate text and user request is just a nice feature.
2. It has only the **Meteor** metric due to its convenience and pleasant output. The **results** vary from theme to theme but are about 30% accurate.
