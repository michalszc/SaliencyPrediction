# MD-SEM

## Implementation
### Architecture
In our implementation we follow the original [MD-SEM paper](http://multiduration-saliency.csail.mit.edu/documents/multiduration_saliency.pdf).

As in the original paper, the model consists of three main parts: an encoder, a Temporal Excitation Module (**TEM**) and a decoder.
As an encoder, we use the **Xception** network pre-trained on ImageNet. **TEM** module uses a Long Short Term Memory (LSTM) network to generate scaling vectors that re-weight the feature maps differently for each of T timesteps (where T = 3 in our implementation). For the decoder, we use a simple module consisting of 3 sets of convolution, upsampling layers.

### Training

The model is trained on the **SALICON-MD** generated from the [SALICON](http://salicon.net/challenge-2017/) dataset. 10000 training and 5000 validation images are used. In our experiments with this model we trained it using the Kullback-Leibler divergence loss. As optimizer, we use **Adam** with inital learning rate of 0.0001, which is reduced by a factor of ten every three epochs. Our implementation achieves reasonable results after 5 epochs.

### Evaluation

|   Dataset             | AUC   | CC   | KLDiv   | NSS  | SIM  |
|-----------------------|-------|------|---------|------|------|
|   SALICON-MD          | 0.9030  | 0.7540 | 0.3831 | 1.4521 | 0.6879 |
|   CodeCharts1k        |  0.8421 |  0.5670 |  0.9728 | 1.8454 | 0.4857 |


## Getting started
Pre-trained versions of the model are available [here](https://aghedupl-my.sharepoint.com/:f:/g/personal/michalszc_student_agh_edu_pl/ElVcKYYS_1BHtNhXlaB8HPEBw1rTs-vYIlfsCHSh5ucvjA?e=Bu5tmZ). Use the created notebooks to try out the model, making sure to change the model location path. If you want to train it yourself, download the **SALICON** dataset and generate **SALICON-MD** based on the [Tempsal code](https://github.com/IVRL/Tempsal?tab=readme-ov-file#data).
