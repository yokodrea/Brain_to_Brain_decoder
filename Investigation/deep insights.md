# (Post submission investigation)

## Still working on futher analysis on main goal

### **Post Investigation Metric Results**

**We have really got really fascinating result in block split in contrast of  random split**

 KNN decoder  accuracy for shuffle control:  **0%**

 KNN decoder accuracy for main model: **0%**


 goodness of fit score (supervised model on train set) : **74%**

 goodness of fit score (supervised model on test set) : **-0.02** *(error)*

 goodness of fit score ( shuffle control on train set) : **-2.87** *(error)*     

 goodness of fit score (shuffled control test set) :  **-1.09** *(error)*


 Now this makes us question further on our previous ?

 So let's start with Why 99% on random split and why** 0%** on block split ? if read the blog you might know . our model is cheating  by memorizing the train data and  outputting the test value of the nearest training example **Nearest neighbours interpolation**

So we avoid this by doing **block split** or **stratified splitting techniques** or other techniques for decorrelating the data.


> Splitting data into training, validation, and test sets, is one of the most standard ways to test model performance in supervised learning settings. [Standford blog](https://datascience.stanford.edu/news/splitting-data-randomly-can-ruin-your-model)

Since our data has high autocorrelation (positive affect convo before negative affect convo order ). Due to this factor we can see on our previous analysis result where the main model accuracy **99%** This is due to data leakage (temporal leakage) Our data has temporal structure when we remove that we can see our model can't cheat anymore 

So the previous limitation is not valid ? No, it's vaild generalization comes under the big picture if we look at the complete outcome we want to whether our model is dyad-specific (idiosyncratic) or cross subject generalization Since our data N=1 which is small. 

So now Temporal leakage/Temporal alignment of EEG data which is segmental limitation of our big picture. Not that it can be ignored . It's the limitation of the given dataset.

**"Temporal leakage/Temporal autocorrrelation is a segmental limitation of the dataset. Generalization is the bigger picture limitation."**


## Results Above arises futher questions does our model learned ?(I'm still investigating this part I'll update it pretty soon.) 

[CEBRA PAPER](https://arxiv.org/abs/2204.00673)
