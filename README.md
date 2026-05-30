# Automatic Speech Recognition with Synthetic Speech

Can a speech recognizer trained only on synthetic speech match one trained on real
human speech? This project tests that hypothesis end to end. It was built for 11-785
Introduction to Deep Learning at Carnegie Mellon University, as a team project in
which I was an equal contributor.

## The problem it solves

High quality labeled speech data is one of the main bottlenecks for state of the art
speech recognition. Collecting and transcribing human audio is expensive. This project
asks whether synthetic speech, generated automatically from text, can stand in for
that data and still train a speech recognizer of comparable quality.

## What it does

* Generates synthetic speech from text transcripts using a VITS text to speech model.
* Converts the generated audio into MFCC features, the input format the recognizer
  expects.
* Trains a Listen, Attend and Spell (LAS) sequence to sequence model to transcribe
  speech back into text.
* Evaluates the recognizer with Word Error Rate and Levenshtein distance, comparing
  models trained on synthetic versus real speech.

## Stack

* Python, PyTorch
* VITS for synthetic speech generation
* A Listen, Attend and Spell encoder decoder architecture for recognition
* MFCC audio features, with LibriSpeech train-clean-360 transcripts used to replicate
  the results

## Repository layout

* `VITS_synthetic_speech_generation.ipynb`, the synthetic speech generation pipeline.
* `LAS notebook.ipynb`, the speech recognizer, including training and the Word Error
  Rate and Levenshtein distance metrics.
* `IDL_Project___Final_Report.pdf`, the full written report.

## How to run

1. In the VITS notebook, add the transcripts you want to synthesize, then generate the
   `.wav` files and convert them to MFCCs.
2. In the LAS notebook, point the data loader at the MFCCs and run training. The
   notebook computes Word Error Rate and Levenshtein distance during training.

To replicate the reported results, use the transcripts from LibriSpeech
train-clean-360.

## Attribution

This was a team project for CMU 11-785. The full author list and report are in
[IDL_Project___Final_Report.pdf](IDL_Project___Final_Report.pdf). This repository is
my copy of the team's work, kept public as a record of my contribution.
