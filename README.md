# Bird-Song-Analysis-Using-Deep-Learning
Analyzing the audio files for detected features have become a lot easier to do with machine learning in the recent years. These kinds of problems not only can be very accurate but also can be performed in scale. 
I was lucky to get involved in a project to analyze bird songs.
The problem:
There are hundreds of wav files of bird song recording. The scientist looks at the spectograms and identifies and labels the syllables in songs for each bird. each bird has its unique songs, so the scientist has to develop a unique set of labels for each bird.
This is a laborious effort as the birds are always singing and more and more data becomes available. 
The model here is an attempt to automate the labelling process by learning from the human scientist labels.

Inputs:A folder of wav files (properly names with the name of the bird and the date).
A folder of matlab files (one file for each wav file with the same naming scheme wav file)

Output:
A keras model that can generate labels for any new wav file.
The code can later be extended to generate similar matlab files.

The process:
The files are loaded into python to generate a dictionary of all the labels.
The Audio files have different lengths hence they are padded with zeros to facilitate reading by the neural network.
The audio data are converted to spectogram (a matrix form of audio data that's more suitable to feed into a deep learning model). I'll add more information in the code.

I tried fitting the data on CNNs (Convolutional Neural Networks) with not much luck. However the RNN (Recurrent Neural Networks) are delivering much better results (work in progress).

The RNN starts with a convolution layer to reduce the dimension and feeds into two layers of LSTMs. The output of the second LSTM layer goes into a softmax layer which determines the label for each y. y in the audio point of view being a small time interval (in order of 4000 intervals for a 30 s input audio).

The model hasn't been trained with adequate training data nor time to yield better results, however the small 20 epochs as shown in the code an accuracy of about 75% can be achieved which is already close to the non-expert human performance.
