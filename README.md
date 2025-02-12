# OTA Channel Impulse Response Measurement
Channel Impulse Response Tutorial - 1/31/2025

In this hands-on activity, you will
1. Create an IQ file from PN codes
2. Use Shout to transmit and receive your IQ file between two nodes
3. Cross-correlate the filtered received signal with your original PN code packet to observe the channel impulse response

## Background: Pseudo-noise (PN) Codes
In contrast to the packets transmitted and received with your receiver design in IH3 and HH2, in this activity, you will create, transmit, and receive a BPSK maximum length pseudo-noise (PN) code packet, omitting both the preamble and sync word.

PN codes are generated using a linear feedback shift register (LFSR) and are semi-random sequences that repeat themselves indefinitely. They have a clean auto-correlation function, can be easily phase synchronized even in the presence of noise, and therefore serve as convenient digital communication system test signals [1].

A N-state PN code will have `2^N - 1` bits. The LFSR starts with an initial state N-dimensional vector, which cannot be all zeros but can have any other combination of ones and zeros. It uses specified taps, which are unique depending on the chosen N, to generate different resulting sequences, as shown in Table 2 of [1].

## Instructions

Follow the instructions and code outlined in the [OTA Channel Impulse Response Tutorial Google Colab](https://colab.research.google.com/drive/1QZAUbmQRLhNf4-C5YXoAXVReRZh-8tlL?usp=sharing). This is a read-only notebook so you will need to save a copy to Drive to make edits. 
  * If you prefer to use Jupyter Notebook, this repository includes a `OTA_Channel_Impulse_Response_Tutorial.ipynb` file you can download to follow the instructions and code on your local machine rather than using Google Colab. You will not need to upload your files. Instead, make sure to download the python notebook file into a directory of choice that you'll use as the working directory during the tutorial.

You will need to download `save_iq_w_tx_file.json` for use in this activity.

Run through the code cells in the notebook sequentially. Sections that need you to complete part of the code or some other task will be marked with a 🛑 icon (code to be filled in will also have `### TODO ###` on the line to complete).

You can either download and use the provided Shout data folder in this repository or walk through the tutorial's instructions to run an experiment with resources on POWDER and collect your own data. You can skip the instructions about running the Shout experiment if you choose to use the provided data.

Below is the per-group information to reference for running your Shout experiments. Running the experiment will require multiple terminal windows in addition to having the code open. You can either have each person operate a different task or have a group representative share their screen while walking through the steps.

*Results:* At the end of the notebook, you should have cross-correlation plots that show the channel impulse response for your experiment. You can view other's results in this [Google Docs](https://docs.google.com/document/d/1V2pEICyCiz0p0sV33NMLEAHHvUstUNarXrIf07RETuw/edit?usp=sharing) to compare your channel impulse response to those with varying nodes and transmitted PN code packets.


| Group | Radio/Site Type | Nodes | Frequency Range | TX/RX Gains | Cluster |
| ----- | --------------- | ----- | --------------- | ----------- | ------- |
| 1     | CBAND X310/Rooftop | MEB, Browning, [3] d430 | 3385-3390 MHz | TX: 27.0, RX: 30.0 | Emulab |
| 2     | CBAND X310/Rooftop | USTAR, Hospital, [3] d430 | 3390-3395 MHz | TX: 27.0, RX: 30.0 | Emulab |
| 3     | CBAND X310/Rooftop | BES, FM, [3] d430 | 3395-3400 MHz | TX: 27.0, RX: 30.0 | Emulab |
| 4     | Dense Site NUC+B210/Dense Deployment | NC Mario, Moran, [3] d430 | 3400-3405 MHz | TX: 85.0, RX: 70.0 | Emulab |
| 5     | Dense Site NUC+B210/Dense Deployment | EBC, Guest House, [3] d430 | 3415-3420 MHz | TX: 85.0, RX: 70.0 | Emulab |
| 6     | Dense Site NUC+B210/Dense Deployment | NC Wasatch, USTAR, [3] d430 | 3420-3425 MHz | TX: 85.0, RX: 70.0 | Emulab |

## References

[1] R. N. Mutagi. Pseudo noise sequences for engineers. Electronics & Communication Engineering Journal, 8(2), April 1996.
