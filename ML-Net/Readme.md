# SALICON

## Implementation
### Architecture
In our implementation we follow the original [ML-Net paper](https://aimagelab.ing.unimore.it/imagelab/pubblicazioni/2016-icpr-saliency.pdf) with several minor changes.

Model is based on the VGG-19 model for image recognition. That model is reduced by flattening layers at the end, and features maps are extracted on 3 levels in CNN part of VGG-19 network. They go by another CNN and then prior mask is applied. At the end the predicted silency map is scaled using bicubic interpolation. 

### Training

The model is trained on the [SALICON](http://salicon.net/challenge-2017/) dataset. Only 1000 training and 500 validation images are used. In our experiments with this model we trained it using the binary cross-entropy loss. As optimizer, we use **SGD** with fixed learning rate of 0.001 and nestrov momentum of 0.9. Our implementation achieves reasonable results after 40 epochs.

### Evaluation
TO DO

|                       |       |      |         |      |      |
|-----------------------|-------|------|---------|------|------|
|                       | AUC   | CC   | KLDiv   | NSS  | SIM  |
|                       |       |      |         |      |      |


## Getting started
Pre-trained versions of the model are available [here](https://aghedupl-my.sharepoint.com/:f:/g/personal/michalszc_student_agh_edu_pl/ElVcKYYS_1BHtNhXlaB8HPEBw1rTs-vYIlfsCHSh5ucvjA?e=Bu5tmZ). Use the created notebooks to try out the model, making sure to change the model location path. If you want to train it yourself, download the SALICON dataset.
