Download Link: https://assignmentchef.com/product/solved-csci3202-assignment4
<br>
This assignment satisfies learning objective 2 (LO2) as specified in the syllabus. You will apply conceptual knowledge of core AI concepts by implementing AI algorithms, analyzing existing intelligent systems (including humans), and using existing AI tools to solve problems.

<h1>Deliverables</h1>

You will need to submit the following files:

<ul>

 <li>py</li>

 <li>&lt;Identikey&gt;-TrainingData.csv</li>

 <li>&lt;Identikey&gt;_A4_report.pdf</li>

</ul>




<h1>Instructions – MUST READ BEFORE GETTING STARTED</h1>

<ul>

 <li>You may email us your submission at any time to account for upload difficulties to Gradescope and we can mark your submission “as-is” and timestamped with the email receipt time.</li>

 <li><strong>It is your responsibility to ensure that your submission passes the autograder. </strong>Here are common autograder failures:​ ​(1)​ ​code does not run to completion locally; (2) submitting a zipped directory; (3) including any additional libraries other than those specified. ​<strong>We won’t be resolving errors in submissions that cause the autograder to fail.</strong>​ If you’re having trouble passing the autograder come to office hours or post to piazza, or email, but this all needs to be done before the deadline.</li>

 <li>For both parts we have provided initial code, please complete all questions within these files. ​<strong>Do not submit iPython notebooks. </strong></li>

</ul>




<h1>Prerequisites</h1>

For this assignment you will need some additional python libraries. You can install these using pip. You may also need to install the prerequisites for these libraries also. More information can be found on their respective manual pages.




<table width="460">

 <tbody>

  <tr>

   <td width="296">pip install matplotlib, scikit-learn,</td>

   <td width="164">pandas, numpy, pillow</td>

  </tr>

 </tbody>

</table>

​ ​                   ​

<h1>Overview</h1>

The purpose of this assignment is to use a Hopfield network and a Multilayer Perceptron (MLP) to recognize hand-drawn digits. We will focus on discriminating 5s from 2s. It is specifically designed to give you experience with all the necessary steps in designing such a system starting with generating your own data.




<h1>Part 1 – Data Preparation – [1 Pt]</h1>

First, you will prepare the data that will be used to train your models. For this, you will use the 5×5 grids provided in Appendix 1 (end of this document). Draw out the digits 5 and 2, four times each (you can draw on paper or digitally draw), with some variation.




The next step is to digitize the data. For each box a digit crosses through, record a 1 in the corresponding box of the 5×5 grid. Otherwise record a 0. This boolean (0 or 1) grid is used as the training data for your network (see Appendix 2 for an example).




The third step is to format the data so it can be inputted into python. The boolean grid should be saved in row major order in a single row of a CSV file (see Appendix 2). You also need to supply a label – “five”, “two” – so each row is associated with a corresponding label of the digit represented by the row.




See the attached file NewInput.csv for an example of how to format your data for python. The first row contains headers and last column specifies the class label. You will use this file in Part 5 (do not use it before Part 5 except as an example for formatting input files).




You can check your data formatting using the provided function ​<strong>utils.vizualize </strong>​which takes an array of length 25, and displays the corresponding image. See skeleton code for an example.




<h2>What to submit</h2>

<ul>

 <li>Take a picture of your input grids and paste them in the report.</li>

 <li>Submit &lt;Identikey&gt;-TrainingData.csv.</li>

</ul>

<strong>           </strong>

<h1>Part 2 – Hopfield Network – [5 Pts]</h1>

You will now implement, train and test a Hopfield network (see ‘HopfieldNotes.pdf’).




<h2>Implementation [4 points]</h2>

We have provided an initial class structure for you to use.

<ul>

 <li><strong>addSinglePattern – </strong>​update your hopfield network with one pattern</li>

 <li><strong>Fit – </strong>update your hopfield network with a list of patterns​</li>

 <li><strong>retrieve – </strong>​takes an input pattern as a parameter and uses your hopfield network to return a retrieved pattern. If necessary you should set your own stopping criteria.</li>

 <li><strong>Classify – </strong>​take an input pattern as a parameter, use your retrieve method, then return a string classification of either “two”, “five” or “unknown”.</li>

</ul>

<strong>Hint</strong>​: You can do this by comparing the retrieved pattern to the ‘perfect’ patterns provided on lines 6 and 7




<h2>Train and Test</h2>

Once you have implemented the Hopfield network, you should fit it on the two ‘perfect’ patterns provided in the code. You should then attempt to classify each of the instances in your &lt;Identikey&gt;-TrainingData.csv file by using them as retrieval cues in the Hopefield network.




<strong>Training Data:            </strong>The two ‘perfect instances provided in the code (lines 6 and 7)

<strong>Test Data:                  </strong>All of ​ ​&lt;Identikey&gt;-TrainingData.csv

<strong>Cross Validation:       </strong>None since we have separate training and testing sets




<h2>In your report [1 point]</h2>

<ul>

 <li>How accurately did your network classify the digits? ​<em>You may use percent accuracy as the metric since the classes are evenly balanced. </em></li>

 <li>If it is making errors, analyze the results in order to understand where the Hopfield network is making errors and explain them in your report. If it is not making errors, then discuss why it is classifying perfectly.</li>

</ul>




<strong>           </strong>

<h1>Part 3 – Train a MLP – [1 Pt]</h1>

Using your generated dataset implement a MLP classifier ​<a href="https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPClassifier.html#sklearn.neural_network.MLPClassifier">using the function provided in</a> <a href="https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPClassifier.html#sklearn.neural_network.MLPClassifier">scikitLearn</a>​ and the default parameters [0.5 points]




<strong>Training Data:            </strong>The two ‘perfect instances provided in the code (lines 6 and 7)

<strong>Test Data:                   </strong>All of &lt;indentikey&gt;-TrainingData.py

<strong>Cross Validation:       </strong>None since we have separate training and testing sets




<h2>In your report [0.5 points]</h2>

<ul>

 <li>How accurately did your network classify the digits?</li>

 <li>If it is making errors, analyze the results in order to understand where the MLP is making errors and explain them in your report. If it is not making errors, then discuss why it is classifying the data perfectly.</li>

</ul>

<h1>Part 4 – Distortion – [2 Pts]</h1>

Perform an experiment to test the effect of distortion your Hopfield Network (from part 2) and MLP (from part 3) when multiple levels of noise is introduced.




<h2>Distorting Your Input</h2>

We have provided a skeleton function to perform the distortion on each instance, complete this function first.




<strong>distort_input </strong>​takes as parameters one instance and a distortion rate, which should be a float between 0 and 1. This is similar to mutation rate in an earlier assignment. For each bit in the input array, if distortion rate is 0.1, there is a 0.1 probability that the bit will be flipped (1 changes to 0 and 0 to 1).




<h2>Experiments</h2>

Once you have implemented the functions, you will experiment with how distortion rate impacts your classifier accuracy. You will distort the instances from ​<strong>&lt;indentikey&gt;-TrainingData.py</strong> using distortion rates ranging from 0 to 0.5, in increments of 0.01. For each distortion rate, train your hopfield network (from part 2), and MLP (from part 3) on ​<strong>undistorted ‘perfect instances’ </strong>(from parts 2 and 3) and then attempt to classify the distorted instances. You should then calculate the accuracy for each classifier at each distortion rate.




<em>As you increase the distortion rate at each step of your testing make sure you are passing undistorted data to your distortion function and are only changing the distortion rate. If you pass previously distorted data then you will quickly end up with data that is all noise.  </em>




<strong>Training Data:            </strong>The two ‘perfect instances provided in the code (lines 6 and 7) <strong>Test Data: </strong>Distorted instances

<strong>Cross Validation:       </strong>None since we have separate training and testing sets




<h2>In your report</h2>

<ul>

 <li>Produce a line plot, with classifier accuracy on the y axis, and distortion rate on the x axis. Your line plot should have two lines, one for your hopfield network and one for your MLP.</li>

 <li>Provide a brief (1 to 2 sentences) commentary on your graph. What does this data tell you about the two methods robustness to distortion.</li>

</ul>

<h1>Part 5 – Experimenting with number of hidden layers [1 Pt]</h1>

We have provided some additional data points in NewInput.csv. You should combine this with your &lt;indentikey&gt;-TrainingData.py and build a MLP where you vary the number of layers and assess whether this improves performance on the distorted data.




<strong>Train:                          </strong>&lt;indentikey&gt;-TrainingData.py + NewInput.csv

<strong>Test</strong>​:                            Distorted instances

<strong>Cross Validation:       </strong>None since we have separate training and testing sets




<h2>In your report [1 point]</h2>

<ul>

 <li>Report the results from your experiments with number of layers. Specifically, reproduce the graph from Part 4, but now with an additional line for different versions of your MLP (You still need to include the graph from Part 4 separately in your report). Briefly discuss your findings.<strong>       </strong></li>

</ul>

<h2>APPENDIX 1 : Data Collection Grids</h2>




<h2>APPENDIX 2 : How to prepare Data Grids</h2>

<ol>

 <li>Write the digit in the grid</li>

</ol>




​




<ol start="2">

 <li>Record the state of the cells (1 if black, 0 if white) in a grid</li>

</ol>

<table width="115">

 <tbody>

  <tr>

   <td width="23">0</td>

   <td width="23">1</td>

   <td width="23">1</td>

   <td width="23">1</td>

   <td width="23">0</td>

  </tr>

  <tr>

   <td width="23">0</td>

   <td width="23">0</td>

   <td width="23">0</td>

   <td width="23">1</td>

   <td width="23">0</td>

  </tr>

  <tr>

   <td width="23">0</td>

   <td width="23">0</td>

   <td width="23">1</td>

   <td width="23">1</td>

   <td width="23">0</td>

  </tr>

  <tr>

   <td width="23">0</td>

   <td width="23">0</td>

   <td width="23">0</td>

   <td width="23">1</td>

   <td width="23">0</td>

  </tr>

  <tr>

   <td width="23">0</td>

   <td width="23">1</td>

   <td width="23">1</td>

   <td width="23">1</td>

   <td width="23">0</td>

  </tr>

 </tbody>

</table>




<ol start="3">

 <li>Convert the grid to row major form and save as a CSV file.</li>

</ol>




<table width="600">

 <tbody>

  <tr>

   <td width="24">0</td>

   <td width="24">1</td>

   <td width="24">1</td>

   <td width="24">1</td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">1</td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">1</td>

   <td width="24">1</td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">1</td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">1</td>

   <td width="24">1</td>

   <td width="24">1</td>

   <td width="24">0</td>

  </tr>

 </tbody>

</table>




<ol start="4">

 <li>Check in visualizer</li>

</ol>































<strong>             </strong>

<h2>APPENDIX 3 : Scoring Rubric</h2>

The scoring rubric​<strong> for your report</strong>​ is based on the Kentucky General Scoring Rubric from the Kentucky Department of Education (KDE).


