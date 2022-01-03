<h1>RGIFE2</h1>

Python codes used to select the reduced set of genes indicative of the cluster in the transcriptional landscape. It is an update version of RGIFE http://ico2s.org/software/rgife.html. The updates include:
- Changed from Python2 to Python3
- Added the 6 folds and 8 folds cross-validation for *validation* in rgife configuration, i.e. Validation: [6CV,8CV, 10CV]
- Changed the options for *cs_rf* which decides cost sensitive learning setting for the random forest in rgife configuration as cs_rf(manual, auto, no), where 'no' means cost sensitive learning (default), 'manual' means using the user-defined class cost, and 'auto' means using the sklearn class costs calculation for auto balance: n_samples / (n_classes * np.bincount(y))
- Added the calculations for recall, precision. Made the calculation of auc suitable for multiple classes model.  
- Modified policies.py which is used to select the final solution from multiple runs of RGIFE. Apart from the min-model, max-model, union-model, we added the calculation of the optimin-model that selects the solution with smallest size and best performance and the optiunion-model that combines all the solutions smaller than threshold size. Print the summaries of multiple solutions, including the frequencies of features selected across multiple runs, the performance and panel size  of each run size.

Required libraries: NumPy, SciPy, Scikit-learn, os, time, sys, subprocess, random, warnings, collections, operator, pandas, tarfile

Run RGIFE multiple times please set the working subdirectory as run$repeat_ID, for example:
```
python ./rgife.py <working directory>/run$repeat_ID/ <config file> <data file>
```
Get the statistic of multiple RGIFE runs and the solutions chosen on different policies:
```
python ./rgife/policies.py <working directory> <num_runs> <threshold_size>

```
