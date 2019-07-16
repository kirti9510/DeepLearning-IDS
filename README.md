# Deep Learning - IDS

Towards Developing a Network Intrusion Detection System using Deep Learning Techniques

## Dataset

-   Orginial dataset downloaded from: https://www.unb.ca/cic/datasets/ids-2018.html
-   once the dataset was downloaded using AWS CLI as instructed in the source, there were 7 csv files that were preprocessed and labelled
-   there were also original network traffic data in .pcap format and logs that are ignored for this study
-   this project uses the dataset remained after cleanup

## Data Cleanup

-   dropped rows with Infinitiy values
-   some files had repeated headers; dropped those
-   converted timestamp value that was date time format: 15-2-2018 to UNIX epoch since 1/1/1970
-   separated data based on attack types for each data file
-   bout 20K rows were removed as a part of data cleanup
-   see data_cleanup.py script for this phase

## Dataset Summary

| File Name      | Traffic Type     | # Samples |
| -------------- | ---------------- | --------: |
| 02-14-2018.csv | Benign           |    663808 |
|                | FTP-BruteForce   |    193354 |
|                | SSH-Bruteforce   |    187589 |
| 02-15-2018.csv | Benign           |    988050 |
|                | DOS-GoldenEye    |     41508 |
|                | DOS-Slowloris    |     10990 |
| 02-16-2018.csv | Benign           |    446772 |
|                | Dos-SlowHTTPTest |    139890 |
|                | DoS-Hulk         |    461912 |
| 02-22-2018.csv | Benign           |   1042603 |
|                | BruteForce-Web   |       249 |
|                | BruteForce-XSS   |        79 |
|                | SQL-Injection    |        34 |
| 02-23-2018.csv | Benign           |   1042301 |
|                | BruteForce-Web   |       362 |
|                | BruteForce-XSS   |       151 |
|                | SQL-Injection    |        53 |
| 03-01-2018.csv | Benign           |    235778 |
|                | Infiltration     |     92403 |
| 03-02-2018.csv | Benign           |    758334 |
|                | BotAttack        |    286191 |

| Traffic Type     | # Samples |
| ---------------- | --------: |
| Benign           |   5177646 |
| FTP-BruteForce   |    193354 |
| SSH-BruteForce   |    187589 |
| DOS-GoldenEye    |     41508 |
| Dos-Slowloris    |     10990 |
| Dos-SlowHTTPTest |    139890 |
| Dos-Hulk         |    461912 |
| BruteForce-Web   |       611 |
| BruteForce-XSS   |       230 |
| SQL-Injection    |        87 |
| Infiltration     |     92403 |
| BotAttack        |    286191 |
| Total Attack     |   1414765 |

# Deep Learning Frameworks

-   perfomance results using various deep learning frameworks are compared
-   10-fold cross-validation techniques was used to validate the model

## Fastai

-   https://www.fast.ai/
-   uses pytorch as the backend

## Keras

-   https://keras.io/
-   using Tensorflow and Theano as backend
-   https://www.tensorflow.org/
-   https://github.com/Theano/Theano

## Pytorch

-   https://pytorch.org/
-   use Pytorch framework straight

# Results

| Dataset     | Framework         | Accuracy (%) | Std-Dev | CPU Time (~mins) |
| ----------- | ----------------- | :----------: | :-----: | :--------------: |
| 02-14-2018  | Fastai            |    99.85     |  0.07   |        \*        |
| 02-14-2018  | Keras-Tensorflow  |    98.80     |   \*    |        \*        |
| 02-14-2018  | Keras-Theano      |      \*      |   \*    |        \*        |
| 02-14-2018  | Pytorch           |      \*      |   \*    |        \*        |
| 02-15-2018  | Fastai            |    99.98     |  0.01   |        25        |
| 02-15-2018  | Keras-Tensorfflow |    99.32     |   \*    |        \*        |
| 02-15-2018  | Keras-Theano      |      \*      |   \*    |        \*        |
| 02-15-2018  | Pytorch           |      \*      |   \*    |        \*        |
| 02-16-2018  | Fastai            |    100.00    |  0.00   |        16        |
| 02-16-2018  | Keras-Tensorflow  |    99.84     |   \*    |        \*        |
| 02-16-2018  | Keras-Theano      |      \*      |   \*    |        \*        |
| 02-16-2018  | Pytorch           |      \*      |   \*    |        \*        |
| 02-22-2018  | Fastai            |    99.87     |  0.15   |       110        |
| 02-22-2018  | Keras-Tensorflow  |    99.97     |   \*    |        \*        |
| 02-22-2018  | Keras-Theano      |      \*      |   \*    |        \*        |
| 02-22-2018  | Pytorch           |      \*      |   \*    |        \*        |
| 02-23-2018  | Fastai            |    99.92     |  0.00   |       120        |
| 02-23-2018  | Keras-Tensorflow  |    99.94     |   \*    |        \*        |
| 02-23-2018  | Keras-Theano      |      \*      |   \*    |        \*        |
| 02-23-2018  | Pytorch           |      \*      |   \*    |        \*        |
| 03-01-2018  | Fastai            |    87.00     |  0.00   |        5         |
| 03-01-2018  | Keras-Tensorflow  |    72.20     |   \*    |        \*        |
| 03-01-2018  | Keras-Theano      |      \*      |   \*    |        \*        |
| 03-01-2018  | Pytorch           |      \*      |   \*    |        \*        |
| 03-02-2018  | Fastai            |    99.97     |   .01   |        75        |
| 03-02-2018  | Keras-Tensorflow  |    98.12     |   \*    |        \*        |
| 03-02-2018  | Keras-Theano      |      \*      |   \*    |        \*        |
| 03-02-2018  | Pytorch           |      \*      |   \*    |        \*        |
|             |                   |              |         |                  |
| Multiclass  | Keras-Tensorflow  |    94.73     |   \*    |        \*        |
| Binaryclass | Keras-Tensorflow  |    94.40     |   \*    |        \*        |

# Fast.ai Results Details

## Brief Results

| Data File      | Accuracy | Loss    |
| -------------- | -------- | ------- |
| 02-14-2018.csv | 99.99%   | 0.00212 |
| 02-15-2018.csv | 99.86%   | 0.02500 |
| 02-16-2018.csv | 99.97%   | 324160  |
| 02-22-2018.csv | 99.97%   | 0.00221 |
| 02-23-2018.csv | 99.82%   | 0.06295 |
| 03-01-2018.csv | 87.14%   | 0.37611 |
| 03-02-2018.csv | 99.72%   | 0.85127 |

### Confusion Matrices

|                                                      02-14-2018                                                      |                                                      02-15-2018                                                      |                                                      02-16-2018                                                      |
| :------------------------------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------: |
| ![](<https://github.com/rambasnet/DeepLearning-IDS/blob/master/graphics/confusion_matrices/02-14-2018--6-15(1).png>) | ![](<https://github.com/rambasnet/DeepLearning-IDS/blob/master/graphics/confusion_matrices/02-15-2018--6-24(1).png>) | ![](<https://github.com/rambasnet/DeepLearning-IDS/blob/master/graphics/confusion_matrices/02-16-2018--6-15(1).png>) |
|                                                      02-22-2018                                                      |                                                      02-23-2018                                                      |                                                      03-01-2018                                                      |
| ![](<https://github.com/rambasnet/DeepLearning-IDS/blob/master/graphics/confusion_matrices/02-22-2018--6-15(1).png>) | ![](<https://github.com/rambasnet/DeepLearning-IDS/blob/master/graphics/confusion_matrices/02-23-2018--6-15(1).png>) | ![](<https://github.com/rambasnet/DeepLearning-IDS/blob/master/graphics/confusion_matrices/03-01-2018--6-15(1).png>) |

03-02-2018
![](<https://github.com/rambasnet/DeepLearning-IDS/blob/master/graphics/confusion_matrices/03-02-2018--6-15(1).png>)

| Data File | % of Data == Attacks | % Attacks Flagged Correctly | % Benign Flagged Incorrectly |
| --------- | -------------------- | --------------------------- | ---------------------------- |
| 02-14     | 36                   | 100                         | <=1                          |
| 02-15     | n/a                  | n/a                         | n/a                          |
| 02-16     | 57                   | 100                         | <=1                          |
| 02-22     | <=1                  | 1                           | 0                            |
| 02-23     | <=1                  | 62                          | <=1                          |
| 03-01     | 28                   | 73                          | 10                           |
| 03-02     | 27                   | 100                         | <=1                          |

# References

-   Iman Sharafaldin, Arash Habibi Lashkari, and Ali A. Ghorbani, “Toward Generating a New Intrusion Detection Dataset and Intrusion Traffic Characterization”, 4th International Conference on Information Systems Security and Privacy (ICISSP), Portugal, January 2018
