# Post Submission Investigation 

# Metric Results

### We have really got really fascinating result in block split in contrast of  random split**

+ **KNN decoder  accuracy (main model) :**  **0%**
+  **KNN decoder accuracy  (shuffle control) :** **0%**

 + **goodness of fit score (supervised model on train set) :** **74%**

 + **goodness of fit score (supervised model on test set) :** **-0.02** *(error)*

 + **goodness of fit score ( shuffle control on train set) :** **-2.87** *(error)*     

  + **goodness of fit score (shuffled control test set) :**  **-1.09** *(error)* 


 Now this makes us question further on our previous ?

 So let's start with Why **99%** on random split and why **0%** on block split ? if read the blog you might know . our model is cheating  by memorizing the train data and  outputting the test value of the nearest training example **Nearest neighbours interpolation**

So we avoid this by doing **block split** or **stratified splitting techniques** or other techniques for decorrelating the data.


> Splitting data into training, validation, and test sets, is one of the most standard ways to test model performance in supervised learning settings. [Standford blog](https://datascience.stanford.edu/news/splitting-data-randomly-can-ruin-your-model)

Since our data has high autocorrelation (positive affect convo before negative affect convo order ). Due to this factor we can see on our previous analysis result where the main model accuracy **99%** This is due to data leakage (temporal leakage) Our data has temporal structure when we remove that we can see our model can't cheat anymore 

So the previous limitation is not valid ? No, it's vaild generalization comes under the big picture if we look at the complete outcome we want to whether our model is dyad-specific (idiosyncratic) or cross subject generalization Since our data N=1 which is small. 

So now Temporal leakage/Temporal alignment of EEG data which is segmental limitation of our big picture. Not that it can be ignored . It's the limitation of the given dataset.

**"Temporal leakage/Temporal autocorrrelation is a segmental limitation of the dataset. Generalization is the bigger picture limitation."**


--------------------


**A primary cause is training an overly complex model
on a small dataset. The model complexity often matters when we design a machine learning
model. If the model is complex and has many parameters, then it would be much easier to
overfit a small number of samples. So in this case cebra which is a complex model and small dataset N = 1 dyad which makes it easy for our model overfit.**

it is difficult to discriminate the influence of the inherent temporal 
autocorrelation in EEG signals due to the coupling of stimuli-driven neural responses and the 
temporal autocorrelations [Overestimated Decoding Performance Arising from Temporal Autocorrelations in EEG signals](https://arxiv.org/pdf/2405.17024)


Solution : **LODO strategy** and **data spliting strategy**  (it was also mentioned on the cited research paper).

In order to know more about overstimation of decoding performance due to temporal autocorrelations read this to get clear idea [Overestimated Decoding Performance Arising from Temporal Autocorrelations in EEG signals](https://arxiv.org/pdf/2405.17024)




## Experimentation of Parameter optimization :

### **Main Model** 

### for default parameter
 
 KNN accuracy: **0%**
 
 Supervised Train gof : **0.742813240612608**
 
 Supervised Test gof : **-0.01799708731630236**

 ### for max iter = 1000
 
 knn = **0%**
 
 Supervised Train gof : **0.7437666133669849**
 
 Supervised Test gof : **-0.07291564955466598**
 

 ### for max iter = 500
 
 knn = **0%**
 Supervised Train gof : **0.7427407726269804** 
 Supervised Test gof : **-0.1092668382266495**

 

 ### for batch_size = 128 and max_iter = 1000

 knn  : **0%**
 
 Supervised Train gof : **0.7431628675754263**
 
 Supervised Test gof : **-0.039260148604888016**


 ### for max_iter = 500 and batch_size = 128 
 
 knn : **0%**
 
 Supervised Train gof : **0.7440594392757375** 
 Supervised Test gof : **-0.06552703548152428**

 ### for max_iter = 50000 and batch_size = 128
 
 knn : **0%**
 
 Supervised Train gof : **0.7441995184569344** 
 
 Supervised Test gof : **-0.055326441769385934**

 -------

  **"After experimenting various parameter tuning (max_iter: 500-5000, batch_size: 128-512, RobustScaler/StandardScalar), the model consistently achieved **~0.74 train GoF** but negative test GoF and **0% KNN accuracy** *"This confirms that the dataset contains a fundamental temporal confound that cannot be overcome by parameter optimization. The model learns the training data but fails to generalize (**test GoF negative, KNN = 0%**), which proves that the limitation is structural to the dataset, not technical to the implementation."***

 




