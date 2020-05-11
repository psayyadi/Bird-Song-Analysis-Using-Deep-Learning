# Bird-Song-Analysis-Using-Deep-Learning
There are people in the world who analyse bird songs for living. I was lucky to get involved in helping one of them.
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
