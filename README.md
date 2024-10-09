# GRUBF
A Simple Yet Effective GRU-based Neural Beamformer for in-Car Speech Separation.<br>
Take 4 tone zones as an example.<br>
## Model
The structure of the model is as follows:
![image](https://github.com/user-attachments/assets/5a795eca-2201-452c-a662-559177ae0cb9)
### Mainly includes:
- **Input Features**: Take the covariance matrix calculated from the multi-channel noise signal as input features.
- **Frequency Transducer**: Use the "Frequency Transducer" (mainly composed of Conv1D) to reduce the frequency dimension, thereby reducing the computational cost of the narrow-band beamforming calculation.
- **GRU-based**: Through three simple GRU modules, the input features are processed along the spatial, temporal and frequency dimensions respectively to simulate and replace conventional beamforming algorithms (such as Mask-based MVDR or others).
- **MIMO**: Predict the beamforming weights for each zone, thereby reconstructing the signal (speech or silence) for each zone.
- **SA-SI-SDR**: The signals of all zones predicted by the model are concatenated in the time dimension and SI-SDR is calculated with the target signals that have been processed in the same way.

This model has been verified on SA8155P and combined with VAD and K2-KWS to realize the in-car voice interaction algorithm.
