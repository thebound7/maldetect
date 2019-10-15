# OpenSource Assignment 3
Sejong University 17011620 Jeong Jaewoo.

I edited [this](https://github.com/llSourcell/antivirus_demo) source code to work it in my local environment.

When training malware data set, I used [this](https://github.com/thebound7/maldetect/blob/master/data.csv) file.

When testing malware or not, I used [CVE-2018-4878 exploit PE Malware](https://github.com/InQuest/malware-samples/blob/master/CVE-2018-4878-Adobe-Flash-DRM-UAF-0day/pe-e1546323dc746ed2f7a5c973dcecc79b014b68bdd8a6230239283b4f775f4bbd) and calc.exe.

## Train
```
$ python learning.py
Researching important feature based on 54 total features

/usr/local/lib/python2.7/dist-packages/sklearn/ensemble/forest.py:246: FutureWarning: The default value of n_estimators will change from 10 in version 0.20 to 100 in 0.22.
  "10 in version 0.20 to 100 in 0.22.", FutureWarning)
14 features identified as important:
1. feature Machine (0.178171)
2. feature Characteristics (0.119501)
3. feature SectionsMaxEntropy (0.113135)
4. feature ResourcesMinEntropy (0.094278)
5. feature DllCharacteristics (0.077378)
6. feature VersionInformationSize (0.060213)
7. feature Subsystem (0.036220)
8. feature ImageBase (0.032229)
9. feature SizeOfOptionalHeader (0.029276)
10. feature MajorSubsystemVersion (0.027682)
11. feature MajorOperatingSystemVersion (0.026289)
12. feature SectionsMeanEntropy (0.020266)
13. feature ResourcesMaxEntropy (0.019064)
14. feature MinorLinkerVersion (0.018625)

Now testing algorithms
GNB : 70.246288 %
DecisionTree : 99.051068 %
RandomForest : 99.366172 %
AdaBoost : 98.652662 %
GradientBoosting : 98.830134 %

Winner algorithm is RandomForest with a 99.366172 % success
Saving algorithm and feature list in classifier directory...
Saved
False positive rate : 0.531092 %
False negative rate : 0.876339 %
```

## Test
```
$ python checkpe.py malware.exe
The file malware.exe is malicious
```
```
$ python checkpe.py calc.exe
The file calc.exe is legitimate
```
