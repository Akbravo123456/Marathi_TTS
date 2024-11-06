This project demonstrates training a Text-to-Speech (TTS) model in Marathi using the VITS architecture from the transformers library. The code takes a dataset of Marathi text segments and corresponding audio durations, tokenizes the text, and trains a TTS model to generate synthetic audio waveforms.

Requirements
To run this code, install the following dependencies:
!pip install torch torchaudio phonemizer
!pip install soundfile
!pip install sentencepiece

Code Overview
Dataset Loading:

Load and parse the data from a JSON file containing Marathi text segments.
Extract text, start times, end times, and calculate durations for each segment.
Tokenization:

Initialize the VitsTokenizer and VitsModel from the transformers library using the Facebook MMS TTS model checkpoint.
Tokenize the text segments for input to the model.
Dataset Preparation:

Define a custom MarathiTTSDataset class, which includes text and duration information.
Tokenize the text in the __getitem__ method for easy batch processing.
Use DataCollatorWithPadding to dynamically pad tokenized sequences during batching.
Data Loading:

Create a DataLoader to feed batches of data into the model during training.
Training Loop:

Initialize the optimizer (Adam) with a learning rate of 1e-4.
Define the loss function as Mean Squared Error (MSELoss) to measure the discrepancy between generated and target audio waveforms.
For each epoch:
Tokenized text sequences are passed to the TTS model.
The model generates waveform outputs.
Compute the loss between generated and target waveforms.
Perform backpropagation and update model parameters.
