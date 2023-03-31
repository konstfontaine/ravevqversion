# VQ-RAVE: Vector Quantized-Realtime Audio Variational autoEncoder

This is an implementation of a vector quantized version of the official _RAVE (Realtime Variational autoEncoder)_ model that was presented by Antoine Caillon and Philippe Esling. 

In the following their paper original paper: ([article link](https://arxiv.org/abs/2111.05011))

## Installation

RAVE needs `python 3.9`. Install the dependencies using

```bash
pip install -r requirements.txt
```

## Preprocessing

RAVE comes with two command line utilities, `resample` and `duration`. `resample` allows to pre-process (silence removal, loudness normalization) and augment (compression) an entire directory of audio files (.mp3, .aiff, .opus, .wav, .aac). `duration` prints out the total duration of a .wav folder.

## Training

For most users the recommandation is to use the `cli_helper.py` script, since it will generate a set of instructions allowing the training and export of both RAVE and the prior model on a specific dataset.

```bash
python cli_helper.py
```

However, alternatively also the `train_{rave, prior}.py` and `export_{rave, prior}.py` scripts can be used manually.

## Reconstructing audio

Once trained, you can reconstruct an entire folder containing wav files using

```bash
python reconstruct.py --ckpt /path/to/checkpoint --wav-folder /path/to/wav/folder
```

You can also export RAVE to a `torchscript` file using `export_rave.py` and use the `encode` and `decode` methods on tensors.

