# SALICON

## Implementation
### Architecture
In our implementation we follow the original [CVPR'15 paper](https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/Huang_SALICON_Reducing_the_ICCV_2015_paper.pdf) with several minor changes.

As in the original paper, the model contains two DNN streams for **fine** and **coarse** processing, in our case we use VGG16 and ResNet-50. Input is resized to 640x480px, exactly size of training dataset. We used the **MaxPooling** layer to reduce the size of the input by half and then pass it to **coarse** stream. The result of the **coarse** stream is resized to match the size of the  **fine** stream. Both outputs are concatenated and convolved with 1×1 filter. The resulting labels (human fixation maps) are 20×15 and are resized to match the size of the input image.

### Training

The model is trained on the [SALICON](http://salicon.net/challenge-2017/) dataset. Only 1000 training and 1000 validation images are used. In our experiments with this model we trained it using the binary cross-entropy loss. As optimizer, we use **SGD** with fixed learning rate of 0.0001 and nestrov momentum of 0.9. Our implementation achieves reasonable results after 100 epochs.

### Evaluation
Checked on SALICON dataset.
|   Model               | AUC   | CC   | KLDiv   | NSS  | SIM  |
|-----------------------|-------|------|---------|------|------|
|   SALICON (VGG-16)    | 0.66  | 0.06 | 1.04    | 0.46 | 0.45 |
|   SALICON (ResNet-50) | 0.63  | 0.18 | 1.05    | 0.80 | 0.49 |


## Getting started
Pre-trained versions of the model are available [here](https://aghedupl-my.sharepoint.com/:f:/g/personal/michalszc_student_agh_edu_pl/ElVcKYYS_1BHtNhXlaB8HPEBw1rTs-vYIlfsCHSh5ucvjA?e=Bu5tmZ). Use the created notebooks to try out the model, making sure to change the model location path. If you want to train it yourself, download the **SALICON** dataset.
