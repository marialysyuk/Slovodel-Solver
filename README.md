# Slovodel-Solver


### Overview

Slovodel  is a Russian version of the well-known [Scrabble](https://en.wikipedia.org/wiki/Scrabble) game. In brief, the rules are as follows. Each participant has 7 letters during his turn, his goal is to make up a word that would give as many points as possible. Rare letters give more points, intersection with the coloured cells give extra points - with the green ones points for the letter are doubled, with the yellow ones points for the letter are tripled, with the blue ones points for the word are doubled, with the red ones points for the word are tripled.

This repository presents the module which automatically recognizes letters, their position on the board and the colour of the cells where the words are situated. All these steps can be combined to calculate the final score of the proposed word automatically. 

There are two main parts in the solution.

#### First part: colour masks

1) Detect four corner points to transform the picture
2) Warp the picture 
3) Detect the center of the board cells
4) Define masks and center of contours
5) Combine masks centers' and cells centers' to define the colour of each cell

#### Detection of the center of the cells
<img src="images/cell_centers.png" alt="drawing" width="700" height ="300"/>

#### Colour masks
<img src="images/masks.png" alt="drawing" width="700" height ="400"/>




#### Second part: letter detection


1) Warp the picture
2) Detect letters contours' with OpenCV function [minAreaRect](https://theailearner.com/tag/cv2-minarearect/)
3) Predict letters with the pretrained [Cyrillic Alphabet Classifier](https://github.com/jlouisle/Machine-Learning-Cyrillic-classifier)
4) Combine cell centers with the predicted letters to understand at what cell of the board you're situated
5) Iterate over the horizontal and vertical rows to detect the whole word
6) Intersect colour grid and letters grid to predict the final score 


#### Detection of the letter contours (at the first picture some letters are groupped into the one blue rectangle, in the second picture this bug is fixed)
<img src="images/letters_detection.png" alt="drawing" width="700" height ="400"/>


#### Initial picture and the proposed prediction
<img src="images/prediction.png" alt="drawing" width="700" height ="400"/>
