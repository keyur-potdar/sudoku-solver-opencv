# sudoku-solver-opencv

Solving Sudoku from images using OpenCV.

### Description
Sudoku is a logic-based, combinatorial number-placement puzzle. The objective is to fill a 9×9 grid with digits so that each column, each row, and each of the nine 3×3 subgrids that compose the grid contain all of the digits from 1 to 9. This project solves any Sudoku puzzle given in an image. The solution is drawn back on the image.

The app is deployed on Heroku using Flask. It can be found at [https://sudoku-solver-opencv.herokuapp.com/](https://sudoku-solver-opencv.herokuapp.com/).

#### Website sample:
![](images/website.png)

### Process
1) Detect the Sudoku grid using some pre-processing and finding contours.
2) Crop the image to get only the Sudoku grid. Align the box properly if it is tilted.
3) Divide the cropped image into a grid of size 9x9 and extract digits from the cells.
4) Predict the digits using CNN. The CNN model was trained on data from the following repository: [https://github.com/wichtounet/sudoku_dataset](https://github.com/wichtounet/sudoku_dataset). It consists of a total of 200 Sudoku images out of which 160 were used for training and 40 were used for testing. To train the CNN, digits were extracted from all the Sudoku images.
5) Solve the Sudoku puzzle using backtracking. Solves even the hardest puzzles in less than 10 milliseconds.
6) Draw the solved puzzle back on the original image.

#### Files:

 - `image_processing_utils.py`: pre-processing image and extraction of digits.
 - `Digit Recognition.ipynb`: training the CNN model to predict digits.
 - `digit_recognition.h5`: saved CNN model.
 - `solver.py`: algorithm to solve the puzzle.
 - `Sudoku.py`: main driver class.
 
### Intermediate steps

1) Pre-processed image   
![](images/sudoku1_preprocessed.jpeg)

2) Cropped image   
![](images/sudoku1_cropped.jpeg) 

3) Extracted digits  
![](images/sudoku1_extracted_digits.jpeg)

4) Solved image  
![](images/sudoku1_solved.jpeg)

The model works on blurred images as well.

![](images/blurry.png)


[This Medium article](https://medium.com/@neshpatel/solving-sudoku-part-ii-9a7019d196a2) gives good insight into how to extract digits from an image.
