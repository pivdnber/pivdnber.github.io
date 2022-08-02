---
layout: single
title: Machine Learning Literature Update
excerpt: Using Machine Learning to classify biomechanics papers published in the last week
header:
  teaser: ML.gif
collection: project
author_profile: false
share: true
layout: splash
---
<br>
For over 20 years, people in the Biomechanics community have searched publication databases for relevant articles, categorized them, and shared them with the Biomch-L community in the form of a weekly [Literature Update](https://biomch-l.isbweb.org/forums/7-Literature-Update). The first Literature Update post was by Dr. Rodger Kram in 1998 (at 2:02am!): 

>Biomch-Lers:  
UC Berkeley library allows campus users to have free use of the Current  
Contents data base.  
I have coupled this directly to my e-mail so that once per week the UC system  
conducts an automatic search of the data base for specified keywords etc.  
and sends me the updated results by e-mail.  
><br>
>Relevent to this list, I search the keywords "biomechanics OR locomotion".  
This has made me aware of the breadth of biomechanics and also of articles  
in journals that I don't subscribe to and seldom scan. I think that  
this could be useful to a significant number ofl of Biomch-L users, and  
having received the blessings of the list moderators, I will begin posting  
my "weekly update" to Biomch-L.  
><br>
>One thing that I have learned is that there is a tremendous amount of  
research taking place on the biomechanics and "locomotion" of cells and  
organelles within cells. Biomch-L deals mostly with the organ or organism  
scale of things. Similarly, many "locoomotion" hits are for studies of  
pharmacological effects on rats. Locomotion is apparently used as an index  
or assay of drug effect.  
><br>
>I post these references only in an effort to give something back to  
Biomch-L. If you find these posts annoying, let me know. If you find them  
useful and want me to continue, let me hear that too.  
><br>
>Rodger 

<br>
What stands out to me about Rodger's post was that he found a way to automate part of the literature search and wanted to give something back to Biomch-L. I find myself in a similar place 20 years later. I want to further automate the weekly Literature Update by using ~~magic~~ Machine Learning:  
<br>  
![Machine Learning is Magic](/images/ML.gif){: .align-center}  
<br>  
While parts of the current Literature Update process are automated, there is still a significant time commitment required to go through the papers, double checking and re-categorize them. Thanks to those who have maintained the Literature Updates over the years, there are years of weekly Literature Updates containing paper titles and their assigned category. 
<br>  
I was able to convince another graduate student, Gary Bruening, that using machine learning to classify papers was an interesting idea. He wrote a python script that crawls through the Literature Updates and parses out the paper's information (title, authors, assigned category, etc.). Gary was able to compile over 37,000 biomechanics papers published since 2010 and each of them were already categorized! We took a supervised learning approach as we liked the current Biomch-L categories and 37,000 papers provided a reasonably-sized dataset to train the classification model. 
<br>  
We compared multiple classification Machine Learning algorithms and created a python script that searches PubMed for biomechanics-related papers published in the last week using Rodger's original keywords: `'Biomech*[Title/Abstract] OR locomot*[Title/Abstract]'`. Then we used the top-performing model to classify the papers pulled from PubMed. Lastly, a script compiles the search results, formats their citations, and organizes them by the predicted category. The end product is a Literature Update like what can be found [here!](https://alcantarar.github.io/literature/) 
<br>  
![confusion_matrix](/images/biomchL_predict_plot_DNN.png){: .align-center}  
<br>
Right now the model has a prediction accuracy of approximately 74% when we test it on a subset of data from Biomch-L. 74% accuracy might not seem very good, but many papers can be reasonably classified into more than one category while still not being the "correct" category. Not entirely satisfied with 74% accuracy, we're still trying new methods of preprocessing the text data and tuning algorithm parameters. If you're interested in learning more about this project, the code and data used are located in my github repository: [www.github.com/alcantarar/literature_update/](https://github.com/alcantarar/literature_update/).



