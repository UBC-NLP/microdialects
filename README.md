# microdialects
Documenting work on micro-dialects

## Attention Viz:

 *Note:* Transliteration is in Habash-Soudi-Buckwalter


### (1) Example of Correctly Identified Micro-Dialect

  
---

![image_25](https://github.com/UBC-NLP/microdialects/blob/master/attenttion_viz/25.png)


| Gold label: Asuit (Egypt) | Predicted label: Asuit (Egypt)|
|-------------------------- | ------------------------------|


**Sentence:** ```يخرب بيت مطنك. غورت الرادل في داهية.```

**Transliteration:** ```yxrb byt mTnk. γwrt AlrAdl fy dAhyħ.```

**Eng:** ```What a devil! You screwed the guy.```

**Attention Description:** ```Attention layer #3 of the model (counting from zero) has several heads attennding to lexical micro-dialectal cues related to the city of Asuit (Egypt). Most notably, lexical cues related to the correct city are attended to. Namely, the word "مطنك" (part of the metaphorical expression meaning "what a devil") recieves attention in heads 1-3, and the word "الرادل" ("man" in city of Asuit) recieves attention in head 2.```





---
