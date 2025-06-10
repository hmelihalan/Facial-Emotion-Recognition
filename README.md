**1.**    **Architecture**

·         **Deep Hierarchical Features**: The increasing number of filters allows the model to learn low-level (edges, textures) to high-level (expressions) features effectively.

·         **Batch Normalization**: Stabilizes training and accelerates convergence.

·         **Dropout Layers**: Regularizes the network and reduces overfitting.

·         **Balanced Depth**: 4 convolutional blocks offer a good trade-off between capacity and overfitting risk.

·         **Input-Specific Design**: It works well with `48x48` grayscale emotion datasets like FER2013.

![[Pasted image 20250610215022.png]]

						Figure 1 – Complex Model Flowchart
**2.**    **Dataset**
  
I used the FER-2013 dataset, which contains grayscale images (48x48 pixels) categorized into 7 emotion classes: Angry, Disgust, Fear, Happy, Sad, Surprise, Neutral. 

|   |   |
|---|---|
|Emotion|Count|
|Angry|4,953|
|Disgust|547|
|Fear|5,121|
|Happy|8,989|
|Sad|6,077|
|Surprise|4,002|
|Neutral|6,198|
|Total|35,887|
							Table 1 - Dataset statistics.
Angry                     Fear                                                 
![[Pasted image 20250610215201.png]]
 Disgust
![[Pasted image 20250610215320.png]]
Fear
![[Pasted image 20250610215326.png]]
Happy
![[Pasted image 20250610215334.png]]
Sad
![[Pasted image 20250610215339.png]]
Surprise
![[Pasted image 20250610215343.png]]
Neutral
![[Pasted image 20250610215347.png]]

						Figure 2 - Samples from the dataset.

**3.**    **Results and Discussion**

Training Results: 

|               |          |            |                  |                   |
| ------------- | -------- | ---------- | ---------------- | ----------------- |
|               | Accuracy | Final Loss | Train Time/Epoch | Epochs To Plateau |
| Simple Model  | 47.71%   | 1.1215     | 30s              | 16                |
| Complex Model | 69.17%   | 0.8282     | 90s              | 90                |
| Improvement   | 21.46%   | 0.2933     | -60s             | 74                |

					Table 2 - Performance Analysis.

**Key Changes that improved learning**

·         Used more layers to better feature extraction

·         Used BatchNorm for stable training, higher learning rate.

·         Used Dropout   reduce overfitting.

·         Increased channeled depth for learn more specifically

·         Increased fully connected layers to better classify

      
**Model’s accuracy for each emotion**

Angry: 57.9%

Disgust: 51.4%

Fear: 39.9%

Happy: 87.3%

Neutral: 67.0%

Sad: 56.1%

Surprise: 81.2%

**Strong Performers**

Happy (87.3%):

o   Why good?

·         Smile and cheek raising is easily detectable

·         Highly visible features (teeths,wrinkles)

Surprise (81.2%):

o   Why good?

·         Wide eyes andraised eyebrows is are distinct patterns (also the model confused it with happy at some datas since they’re similar assets)

·         Oval mouth shape differs from other emotions

![[Pasted image 20250610215526.png]]
![[Pasted image 20250610215531.png]]![[Pasted image 20250610215543.png]]![[Pasted image 20250610215536.png]]

					Figure 3 – Data samples of high accuracy.

**Weak Performers**

Fear (39.9%):

o   Why bad?

·         Similar face expression to sad and angry (eyebrows, sometimes mouth)

·         With eye widening and scream expression model loses intensity to surprise (sometimes angry)

Disgust (51.4%):

o   Why bad?

·         Disgust expression really similar with nose, mouth, eye and eyebrow shape to angry

·         Mode cannot differ low intensity-anger which we get angry when we disgust from something

![[Pasted image 20250610215715.png]]![[Pasted image 20250610215722.png]]![[Pasted image 20250610215727.png]]![[Pasted image 20250610215731.png]]

						Figure 4 – Data samples of low accuracy.

