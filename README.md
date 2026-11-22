# Image classification for new classes (Transfer learning)

In this project I use a technique called transfer learning for a different image classification than the original model is trained on.
First, EfficientNetV2B0 (6 million parameters) convolutional neural network is used as a frozen base to train the new head, which enables the model to recognize new classes of images. Then,
the model is fine-tuned to improve the accuracy even more, which trains all the layers starting from 100-th till the end. As a result, the model is able to correctly recognize new classes without spending a lot 
of resources training such a model from scratch.

## Dataset

The dataset can be downloaded from https://www.kaggle.com/datasets/puneet6060/intel-image-classification. New classes that the model will learn include: street, sea, mountain, glacier, forest, buildings.
It is split in such fashion: 12k images for train set, 2k images for validation set and 3k images for test set. Images are of size 150x150 px and 3 channels. For better generalization the data is augmented
in this way: flipping, rotation, zoom, contrast.

## Results

The model achieved test set accuracy of 0.9187. Table below shows other metrics: precision, recall, f1 score.

<table>
  <thead>
    <tr>
      <th>Class</th>
      <th>Precision</th>
      <th>Recall</th>
      <th>F1-score</th>
      <th>Support</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>buildings</td><td>0.93</td><td>0.94</td><td>0.93</td><td>437</td></tr>
    <tr><td>forest</td><td>0.99</td><td>1.00</td><td>0.99</td><td>474</td></tr>
    <tr><td>glacier</td><td>0.88</td><td>0.84</td><td>0.86</td><td>553</td></tr>
    <tr><td>mountain</td><td>0.87</td><td>0.85</td><td>0.86</td><td>525</td></tr>
    <tr><td>sea</td><td>0.91</td><td>0.98</td><td>0.94</td><td>510</td></tr>
    <tr><td>street</td><td>0.95</td><td>0.93</td><td>0.94</td><td>501</td></tr>
  </tbody>
  <tbody>
    <tr><td><b>accuracy</b></td><td></td><td></td><td><b>0.92</b></td><td>3000</td></tr>
    <tr><td><b>macro avg</b></td><td>0.92</td><td>0.92</td><td>0.92</td><td>3000</td></tr>
    <tr><td><b>weighted avg</b></td><td>0.92</td><td>0.92</td><td>0.92</td><td>3000</td></tr>
  </tbody>
</table>

Forest and Street classes are recognized the best, while glacier and mountain the worst.
Below is shown a confusion matrix, which visualizes, which classes were confused the most.

<img width="744" height="681" alt="image" src="https://github.com/user-attachments/assets/8a179ec7-ce57-49d0-9491-198141273f2a" />

It is apparent, that mountain and glacier classes were confused the most, which makes a lot of sense, since both have very similar forms.

## Conclusions

To conclude, the model achieved a high test set accuracy and was able to recognize each new class in high accuracy. Most confused classes were mountain and glacier, which is expected.
Both phases of transfer learning succeeded and improved model accuracy for the new classes (see train/val plots in notebook file).

## To run

Download the dataset and copy into /content if you use Google Colab. Install the dependencies and run the notebook if run locally.

