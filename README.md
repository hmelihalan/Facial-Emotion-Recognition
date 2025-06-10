1.	Introduction
This project focuses on facial emotion recognition using grayscale images from the FER-2013 dataset. The goal is to classify emotions such as happy, sad, angry, etc., from facial expressions using a convolutional neural network (CNN). 
We chose this problem because emotional intelligence is essential in human-computer interaction systems, and recognizing facial emotions can significantly improve user experience in real-time applications. Also, as this was our first attempt at deep learning, we found it interesting and educational to observe model behavior and learning dynamics on a well-known benchmark dataset. 

2.	Architecture
•	Deep Hierarchical Features: The increasing number of filters allows the model to learn low-level (edges, textures) to high-level (expressions) features effectively.
•	Batch Normalization: Stabilizes training and accelerates convergence.
•	Dropout Layers: Regularizes the network and reduces overfitting.
•	Balanced Depth: 4 convolutional blocks offer a good trade-off between capacity and overfitting risk.
•	Input-Specific Design: It works well with 48x48 grayscale emotion datasets like FER2013. 
•	 

3.	Dataset
We used the FER-2013 dataset, which contains grayscale images (48x48 pixels) categorized into 7 emotion classes: Angry, Disgust, Fear, Happy, Sad, Surprise, Neutral. 
Emotion 	Count 
Angry 	4,953 
Disgust 	547 
Fear 	5,121 
Happy 	8,989 
Sad 	6,077 
Surprise 	4,002 
Neutral 	6,198 
Total 	35,887 

Angry	  Disgust	   Fear		Happy		Sad	     Surprise	    Neutral 





 

4.	Results and Discussion
Training Results: 

	
Accuracy	
        Final Loss	
Train Time/Epoch	
Epochs To Plateau
Simple Model	
47.71%	
1.1215	
30s	
16
Complex Model	
69.17%	
0.8282	
90s	
90

Improvement	
21.46%	
0.2933	
-60s	
74
Table 2 - Performance Analysis.



Key Changes that improved learning
•	Used more layers to better feature extraction
•	Used BatchNorm for stable training, higher learning rate.
•	Used Dropout   reduce overfitting.
•	Increased channeled depth for learn more specifically
•	Increased fully connected layers to better classify
       Model’s accuracy for each emotion
Angry: 57.9%
Disgust: 51.4%
Fear: 39.9%
Happy: 87.3%
Neutral: 67.0%
Sad: 56.1%
Surprise: 81.2%

Strong Performers
Happy (87.3%):
o	Why good?
•	Smile and cheek raising is easily detectable
•	Highly visible features (teeths,wrinkles)
Surprise (81.2%):
o	Why good?
•	Wide eyes andraised eyebrows is are distinct patterns (also the model confused it with happy at some datas since they’re similar assets)
•	Oval mouth shape differs from other emotions

    




Weak Performers
Fear (39.9%):
o	Why bad?
•	Similar face expression to sad and angry (eyebrows, sometimes mouth)
•	With eye widening and scream expression model loses intensity to surprise (sometimes angry)

Disgust (51.4%):
o	Why bad?
•	Disgust expression really similar with nose, mouth, eye and eyebrow shape to angry
•	Mode cannot differ low intensity-anger which we get angry when we disgust from something

     



5.	Future Work
Shortcomings were definitely on the model building side our model couldn’t differentiate some expressions that looked really alike. Fixed kernels couldn’t be able to approach specific parts of the face when needed to. Dataset was controversial at some datas where you really can’t differ the emotions. 
The improvements in the future should be building a model that can analyze the images with separating the face to eyes, mouth and nose to get more accuracy. To do that we need to search different kernel settings.

If we redesigned this model at the beginning we would’ve choose a latest dataset that categorized better than FER-2013. Maybe focused a bit more on how can training can be made efficient. Or maybe chose a project that the computer can differentiate much better and much easily.
6.	References
7.	Kaggle. FER-2013 Facial Expression Dataset. https://www.kaggle.com/datasets/msambare/fer2013  
8.	  PyTorch Documentation. Loss functions and optimizers. https://pytorch.org/docs/stable/  
9.	  SENG 460 Lecture Materials 

