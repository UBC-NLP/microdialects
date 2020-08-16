# microdialects
Documenting work on micro-dialects

## Attention Viz:

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


![image_3](https://github.com/UBC-NLP/microdialects/blob/master/attenttion_viz/24.png)


| Gold label: Marsa_Matrouh (Egypt) | Predicted label: Tobruq (Libya)|
|-------------------------- | ------------------------------|


**Sentence:** ```العشا اليوم كان عند الشيخ علي حمدي الحداد ، لمؤخذة بقى على الخيانة ، ايش مشاك غادي```

**Transliteration:** ```AlςšA Alywm kAn ςnd Alšyx ςly Hmdy AlHdAd , lmŵxðħ bqý ςlý AlxyAnħ , Ayš mšAk γAdy```

**Eng:** ```Dinner tonight was at Shaikh Ali Hamdi Al-Haddad. Why on earth did you leave[?]```

![image_matrouh_to_tobruq](https://github.com/UBC-NLP/microdialects/blob/master/attenttion_viz/matrouh_to_tobruq.png)


**Explanation:** ```The image Figure above shows that even though the model makes a prediction error here, its error is meaningful in that it chooses a city that is located in the vicinity of gold. Interestingly, the example shows that the city-level model picks a close-by city in a different country, rather than a city in the same country. This probably reflects how micor-dialects paint a more nuanced (and linguistically plausible) picture. This also suggests that country-level dialect models are based on arbitrary assumptions, by virtue of being dependent on political boundaries. We now show an attention visualization of the sentence:```


![image_1](https://github.com/UBC-NLP/microdialects/blob/master/attenttion_viz/25.png)


**Attention Description:** ```Attention layer #3 of the model (counting from zero) has several heads attennding to lexical micro-dialectal cues related to the city of Asuit (Egypt). Most notably, lexical cues related to the correct city are attended to. Namely, the word "مطنك" (part of the metaphorical expression meaning "what a devil") recieves attention in heads 1-3, and the word "الرادل" ("man" in city of Asuit) recieves attention in head 2. These cues usually co-occur with the token "غور" ("you screwed [somebody])", which is also characteristic of the Southern Egyptian region, and the city of Asuit. This is clear in the following image where the token "غور" attends to other micro-dialectal cues in the sequence:```

![image_1](https://github.com/UBC-NLP/microdialects/blob/master/attenttion_viz/25.png)




---
