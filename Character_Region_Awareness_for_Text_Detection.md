# Character Region Awareness for Text Detection
### 1. Related Work: Various Text Detectors
* __Regression-based text detectors:__ <br>
using box regression adapted from object detectors. <br>
having a structural limitation to captureing all possible shapes.
  * TextBoxes
  * DMPNet
  * RDSS(Rotation-Sensitive Regression Detector)
* __Segmentation-based text detectors:__<br>
dealing with segmentation to seek text regions at the pixel level.
  * Multi-scale FCN
  * Holistic-prediction
  * PixelLink
  * SSTD: regression + segmentation (using Attention mechanism)
  * TextSnake: text region + center line
* __End-to-end text detectors:__<br>
trains the detection and recognition module simultaneously so as to enhance detection accuracy by leveraging the recognition result.
  * FOTS
  * EAA
  * Mask TextSpotter
* __Character-level text detectors:__<br>
  * Zhang et al.: using MSER - has limitaions under certain situations(low contrast, curvature, light relection)
  * Yao et al.
  * Seglink
  * WordSup: using a __weakly supervised framework__ to train the character level detector

### 2. Summary
* __Main Objective:__ precisely localize each individual character in natural images.
* __Main Methodology:__<br>
  * train a deep neural network to predict character regions and the affinity between characters.
  * the model is trained in a weakly supervised manner (since there is no public character level dataset available)
* __Architecture:__<br>
  ![Schematic illustration of our network architecture](https://github.com/hestheimar/Paper-Review/blob/master/img/CRAFT_architecture.PNG)
* __Training:__
  1. Ground Truth Label Generation
    * __region score__: probability that the given pixel is the center of the character.
    * __affinity score__: the center probability of the space between adjacent characters.
    * word box confidence map = number of detected characters / number of grount truth characters
