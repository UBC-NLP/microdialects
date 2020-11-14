# Toward Micro-Dialect Identification in Diaglossic and Code-Switched Environment

This repo provides our dataset and models used for ["Toward Micro-Dialect Identification in Diaglossic and Code-Switched Environment"](https://arxiv.org/abs/2010.04900) (Abdul-Mageed et al., 2020). 

The datasets and models are only distributed for research purpose. To access the dataset and model of the paper , please fill out [this registration form](https://docs.google.com/forms/d/e/1FAIpQLSeYw9oQ01fHzeIj_3tdrZu9m8yj5nU7L5IZ8iZLj2zQyHK6FQ/viewform?usp=sf_link). 

We will provide the following datasets and models after submiting the registration form. 
1. We will offer the TRAIN and TEST datasets of 3 splits (i.e., A, B, and C) for each of the narrow, medium, and wide settings. Table 1 shows the distribution of datasets. According to the Twitter distribution restriction, we only provided the tweet IDs and labels of our data. Please acquire tweet content via [Twitter API](https://developer.twitter.com/en). 

<p align="center">
    <img src="https://github.com/UBC-NLP/microdialects/blob/master/image/split3_dis.png" alt>
</p>
<p align="center"> TABLE 1. TRAIN and TEST data sizes and label distribution (in city, state, and country) across the 3 splits for each of the narrow, medium, and wide settings
</p>

2. The best fine-tuned single-task MARBERTA models of three tasks under each setting. We only provide the model that obtained the best F1 score across 3 splits (i.e., A, B, C) under each setting. Table 2. shows the performances of the models. We provide a instruction to help you load the checkpoint and use the fine-tuned model for inference. Please check the [notebook](https://github.com/UBC-NLP/microdialects/blob/master/inference_example/Load_MARBERT.ipynb) and a [sample tsv file](https://github.com/UBC-NLP/microdialects/blob/master/inference_example/inference_sample.tsv) for model inference. 

<p align="center">
    <img src="https://github.com/UBC-NLP/microdialects/blob/master/image/marbert_best.png">
</p>
<p align="center"> TABLE 2. Model Performance on TEST set. For each task, we provide the model that obtained the best F1 score across 3 splits (i.e., A, B, C) under each setting. Epoch indicates the best number of the epoch. 
</p>

----
Citing Guide - please follow the following citation guide if you use any of this work in your research:
```
@inproceedings{abdul-mageed-etal-2020-toward,
    title = "Toward Micro-Dialect Identification in Diaglossic and Code-Switched Environments",
    author = "Abdul-Mageed, Muhammad  and
      Zhang, Chiyu  and
      Elmadany, AbdelRahim  and
      Ungar, Lyle",
    booktitle = "Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing (EMNLP)",
    month = nov,
    year = "2020",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2020.emnlp-main.472",
    pages = "5855--5876",
}
```

----
## Attention Viz:
We visualize attention in ~250 examples from our TEST set using our single-task MARBERT-narrow model fine-tuned in split B in Table 1. We provide visualizations from two examples here. We also collect more examples [here](https://github.com/UBC-NLP/microdialects/tree/master/attenttion_viz). All the visualizations are created via [bertviz](https://github.com/jessevig/bertviz) tool.

*Note:* Transliteration is in Habash-Soudi-Buckwalter

---

### (1) An example of ```correctly``` identified micro-dialect
  
---

![image_24](https://github.com/UBC-NLP/microdialects/blob/master/attenttion_viz/24.png)


| Gold label: Asuit (Egypt) | Predicted label: Asuit (Egypt)|
|-------------------------- | ------------------------------|


**Sentence:** ```يخرب بيت مطنك. غورت الرادل في داهية.```

**Transliteration:** ```yxrb byt mTnk. γwrt AlrAdl fy dAhyħ.```

**Eng:** ```What a devil! You screwed the guy.```

**Attention Description:** ```Attention layer #3 of the model (counting from zero) has several heads attennding to lexical micro-dialectal cues related to the city of Asuit (Egypt). Most notably, lexical cues related to the correct city are attended to. Namely, the word "مطنك" (part of the metaphorical expression meaning "what a devil") recieves attention in heads 1-3, and the word "الرادل" ("man" in city of Asuit) recieves attention in head 2. These cues usually co-occur with the token "غور" ("you screwed [somebody])", which is also characteristic of the Southern Egyptian region, and the city of Asuit. This is clear in the following image where the token "غور" attends to other micro-dialectal cues in the sequence:```

![image_25](https://github.com/UBC-NLP/microdialects/blob/master/attenttion_viz/25.png)


---

### (2) An example of ```wrongly``` identified micro-dialect
  
---


| Gold label: Marsa_Matrouh (Egypt) | Predicted label: Tobruq (Libya)|
|-------------------------- | ------------------------------|


**Sentence:** ```العشا اليوم كان عند الشيخ علي حمدي الحداد ، لمؤخذة بقى على الخيانة ، ايش مشاك غادي```

**Transliteration:** ```AlςšA Alywm kAn ςnd Alšyx ςly Hmdy AlHdAd , lmŵxðħ bqý ςlý AlxyAnħ , Ayš mšAk γAdy```

**Eng:** ```Dinner tonight was at Shaikh Ali Hamdi Al-Haddad. Why on earth did you leave[?]```


![image_matrouh_to_tobruq](https://github.com/UBC-NLP/microdialects/blob/master/attenttion_viz/matrouh_to_tobruq.png)



**Explanation:** ```The Figure above shows that even though the model makes a prediction error here, its error is meaningful in that it chooses a city that is located in the vicinity of gold. The Figure shows how the model confuses the city of Matrouh (Egypt; black circled) with that of Tobruq (Libya; red circled). This means, interestingly, that the city-level model is able to pick a close-by city in a different country than the gold label, rather than a far city in the same country as gold. This reflects how micor-dialects paint a more nuanced (and linguistically plausible) picture. This also suggests that country-level dialect models are based on arbitrary assumptions, by virtue of being dependent on political boundaries which are not always what defines language variation. We now show an attention visualization of the sentence:```


![image_3](https://github.com/UBC-NLP/microdialects/blob/master/attenttion_viz/3.png)


**Attention Description:** ```Attention layer #4 of the model (counting from zero) has several heads attennding to lexical micro-dialectal cues related to the city of Marsa_Matrouh (Egypt). Most notably, the two tokens "ايش" and "مشاك" recieve a great share of the attention in heads 4 and 5, with the first word recieving more weight. Other token in the sentence, such as "الخيانة" also recieve pronounced attention, although this token is shared across dialects and also by MSA. As such, even though the attention weights seem useful, they are not perfect.```

---
