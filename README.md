# Music-Genre-Classification
- Developed by Arpit Maheshwari and Dhruv Mahajan as a coursework assignment at IIIT, Hyderabad.

## Objective
- Refer and implement a Genre Classification System based on the Tzanetakis & Cook (2002) paper [Musical Genre Classification of Audio Signals](https://www.ee.columbia.edu/~dpwe/papers/Tzan02-musgenre.pdf).
- This paper describes the first system developed for this task and has a compilation of several
- Timbral Texture Features, Rhythmic Content Features, and Tonal (Pitch Content) Features.
- The dataset can be found [here](https://www.kaggle.com/carlthome/gtzan-genre-collection)

## Dividing genres into sets
- set1 = ['classical', 'hiphop', 'metal', 'disco', 'reggae']
- set2 = ['pop', 'rock', 'country', 'jazz', 'blues']

## Feature extraction
- Timbral Features: Mean and Variance of Spectral Centroid, Spectral Rolloff, Spectral Flux, Time Domain Zero Crossings, first five Mel-frequency Cepstral Coefficients (MFCC). Also Low Energy Feature is selected. All in all giving a 19 dimension feature matrix. 
- Rhythmic Features: A0, A1: relative amplitude (divided by the sum of amplitudes) of the first, and second histogram peak; RA: ratio of the amplitude of the second peak divided by the amplitude of the first peak; P1, P2: period of the first, second peak in bpm; SUM: overall sum of the histogram (indication of beat strength.
- Pitch Features: Prevalence of Most Common Pitch Class, Interval Between Most Prevalent Pitch Classes and Major-Minor Scale.  

## Outcome
### Comparison: Feature Selection
  * Analysis on Set1 
    - The `highest accuracy` achieved for this set is `94.28%` using an `SVM classifier having Linear Kernel` with `Texture Window` and `Analysis Window` set as `5 sec and 25 msec` respectively. 
    - This accuracy was achieved with keeping only the Timbral features. 
    - It is observed that, for each Analysis Window per Texture Window, SVM classifier gave the highest accuracy with keeping only the Timbral features.
    - On introducing Rhythmic and Pitch features along with Timbral features, the highest accuracy had a slight drop.
  
  * Analysis on Set2
    - The `highest accuracy` achieved for this set is `77.33%` using an `K-NN Classifier` for two pairs of `Texture Window` and `Analysis Window`, <`3 sec, 75 msec`> and <`1 sec, 25 msec`> respectively.
    - This accuracy was achieved with keeping only the Timbral features.
    - It is observed that, for each Analysis Window per Texture Window, K-NN classifier gave the highest accuracy with keeping only the Timbral features.
    - However, it is noteworthy that when Rhythmic and Pitch features were used along with Timbral features, the accuracy had a slight drop and the classifier giving the highest accuracy changed to `Random Forest`. 
  * For both the feature sets, `normalizing` the Timbral, Rhythmic and Pitch features increased the highest accuracy significantly. For example, with `Texture Window` and `Analysis Window` set as `5 sec and 25 msec` respectively, the accuracy with `de-normalized` data was `84.28%` while after `normalizing` it increased to `94.28%`. 

### Comparison: Window Sizes
  * Set1
    - `Texture Window` and `Analysis Window` set as <`5 sec, 25 msec`> respectively, give the highest accuracy.
    - Infact for each texture window, `Analysis Window` of `25 msec` gives the highest accuracy among all the three windows.
    - The accuracy ranges from `85.71% to 94.28%`, over all analysis windows.
  
  * Set2
    - Two `Texture Window` and `Analysis Window` pairs, `3 sec, 75 msec`> and <`1 sec, 25 msec`> respectively, give the highest accuracy.
    - The accuracy ranges from `69.33% to 77.33%`, over all analysis windows.

### Comparison: ML Approach
  * Analysis on Set1
    - `SVM` classifier with `Linear` kernel gives the highest accuracy in each Analysis Window of each Texture Window.
    - `Random Forest` classifier gives the second best accuracy, compared to `SVM` classifier.

  * Analysis on Set2
    - For `Only Timbral Features`, `K-NN` classifier works best giving the highest accuracy for the Analysis Window.
    - As soon as `Rhythmic and Pitch` features are used along with `Timbral`, K-NN performs poorly when compared to `Random Forest`.

  * To summarize, `SVM` performs best for Set1 altogether, while for Set2 `K-NN` works best when only Timbral features are used, else `Random Forest` works best. 
 
