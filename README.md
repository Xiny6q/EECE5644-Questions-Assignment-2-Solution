Download link :https://programming.engineering/product/eece5644-questions-assignment-2-solution/

# EECE5644-Questions-Assignment-2-Solution
EECE5644 Questions Assignment 2 Solution
Question 1 (50%)

The probability density function (pdf) for a 2-dimensional real-valued random vector X is as follows: p(x) = p(xjL = 0)P(L = 0) + p(xjL = 1)P(L = 1). Here L is the true class label that indicates which class-label-conditioned pdf generates the data.

The class priors are P(L = 0) = 0:6 and P(L = 1) = 0:4. The class class-conditional pdfs are p(xjL = 0) = w1g(xjm01; C01) +w2g(xjm02; C02) and p(xjL = 1) = g(xjm1; C1), where g(xjm; C) is a multivariate Gaussian probability density function with mean vector m and covariance matrix C. The parameters of the class-conditional Gaussian pdfs are: w1 = w2 = 1=2, and

m01 = [50 ] C01 = [40 02 ] m02 = [04 ] C02 = [10 03 ] m1 = [32 ] C1 = [20 02 ]

For numerical results requested below, generate the following independent datasets each con-sisting of iid samples from the specified data distribution, and in each dataset make sure to include the true class label for each sample. Save the data and use the same data set in all subsequent exercises.

Dtrain100 consists of 100 samples and their labels for training;

Dtrain1000 consists of 1000 samples and their labels for training;

Dtrain10000 consists of 10000 samples and their labels for training;

D20validateK consists of 20000 samples and their labels for validation;

Part 1: (10%) Determine the theoretically optimal classifier that achieves minimum prob-ability of error using the knowledge of the true pdf. Specify the classifier mathematically and

implement it; then apply it to all samples in D20validateK. From the decision results and true labels for this validation set, estimate and plot the ROC curve of this min-P(error) classifier, and on the ROC

curve indicate, with a special marker, indicate the point that corresponds to the min-P(error) classi-fier’s operating point. Also report your estimate of the min-P(error) achievable, based on counts of

decision-truth label pairs on D20validateK. Optional: As supplementary visualization, generate a plot of the decision boundary of this classification rule overlaid on the validation dataset. This establishes

an aspirational performance level on this data for the following approximations.

Part 2: (20%) (a) Using the maximum likelihood parameter estimation technique, estimate the class priors and class conditional pdfs using training data in Dtrain10000. As class conditional pdf models, for L = 0 use a Gaussian Mixture model with 2 components, and for L = 1 use a single

Gaussian pdf model. For each estimated parameter, specify the maximum-likelihood-estimation objective function that is maximized as well as the iterative numerical optimization procedure used, or if applicable, for analytically tractable parameter estimates, specify the estimator formula. Using these estimated class priors and pdfs, design and implement an approximation of the min-

P(error) classifier, apply it on the validation dataset D20validateK. Report the ROC curve and minimum probability of error achieved on the validation dataset with this classifier that is trained with 10000

samples. (b) Repeat Part (2a) using Dtrain1000 as the training dataset. (c) Repeat Part (2a) using Dtrain100 as the training dataset. How does the performance of your approximate min-P(error) classifier

change as the model parameters are estimated (trained) using fewer samples?

Part 3: (20%) (a) Using the maximum likelihood parameter estimation technique train a logistic-linear-function-based approximation of class label posterior function given a sample. As in part 2, repeat the training process for each of the three training sets to see the effect of training set sample count; use the validation set for performance assessment in each case. When optimizing the


parameters, specify the optimization problem as minimization of the negative-log-likelihood of the training dataset, and use your favorite numerical optimization approach, such as gradient descent or Matlab’s fminsearch or Python’s minimize. Use the trained class-label-posterior approximations to classify validation samples to approximate the minimum-P(error) classification rule; estimate the probability of error that these three classifiers attain using counts of decisions on the validation set. Optional: As supplementary visualization, generate plots of the decision boundaries of these trained classifiers superimposed on their respective training datasets and the validation dataset. (b) Repeat the process described in Part (3a) using a logistic-quadratic-function-based approximation of class label posterior functions given a sample.

Note 1: With x representing the input sample vector and w denoting the model parameter vec-

tor, logistic-linear-function refers to h(x; w) = 1=(1+e

wTz(x)

), where z(x) = [1; x

T T

] ; and logistic-

quadratic-function refers to h(x; w) = 1=(1 + e

wTz(x)

2

2

T

), where z(x) = [1; x1; x2; x1

; x1x2; x2

] .

Hint: The classifier designed in Part 1 uses the true pdf knowledge and achieves theoretically optimum performance in terms of minimizing P(error). The classifiers designed in Part 2 are approximations of the theoretically optimum classification rule using the correct functional form of the data pdf, however the quality of approximation for these generative models will get worse as their parameters are estimated with fewer training samples. The classifiers in Part 3 attempt to directly approximate class label posteriors, and the approximtion capability increases as the model gets more complex (linear to quadratic). The classifiers in Part 3, however, are limited by the approximation capability of their functional form. While the classifiers in Part 2 can asymptotically approach the performance level of the theoretically optimal one if they are trained with more data, the classifiers in Part 3 are bounded in performance by the fact that they can only generate linear or quadratic decision boundaries, so no amount of training data will enable them to asymptotically approximate the theoretically optimal classification rule (which has a classification boundary that is more complex than quadratic).

Question 2 (30%)

A vehicle at true position [xT ; yT ]T in 2-dimensional space is to be localized using distance (range) measurements to K reference (landmark) coordinates f[x1; y1]T; : : : ; [xi; yi]T; : : : ; [xK ; yK ]Tg. These range measurements are ri = dTi + ni for i 2 f1; : : : ; Kg, where dTi = k[xT ; yT ]T [xi; yi]Tk is the true distance between the vehicle and the ith reference point, and ni is a zero mean Gaus-sian distributed measurement noise with known variance si2. The noise in each measurement is independent from the others.

Assume that we have the following prior knowledge regarding the position of the vehicle:

! = (2psxsy)

1

h

“

s2

0

#

1

“

x

#

x

x y

x

2

y

2

p

y

1e

i

0

sy

(1)

where [x; y]T indicates a candidate position under consideration.

Express the optimization problem that needs to be solved to determine the MAP estimate of the vehicle position. Simplify the objective function so that the exponentials and additive/multiplicative terms that do not impact the determination of the MAP estimate [xMAP; yMAP]T are removed appro-priately from the objective function for computational savings when evaluating the objective.

Implement the following as computer code: Set the true vehicle location to be inside the circle with unit radious centered at the origin. For each K 2 f1; 2; 3; 4g repeat the following.

Place evenly spaced K landmarks on a circle with unit radius centered at the origin. Set mea-surement noise standard deviation to 0.3 for all range measurements. Generate K range measure-ments according to the model specified above (if a range measurement turns out to be negative, reject it and resample; all range measurements need to be nonnegative).

Plot the equilevel contours of the MAP estimation objective for the range of horizontal and vertical coordinates from 2 to 2; superimpose the true location of the vehicle on these equilevel contours (e.g. use a + mark), as well as the landmark locations (e.g. use a o mark for each one).

Provide plots of the MAP objective function contours for each value of K. When preparing your final contour plots for different K values, make sure to plot contours at the same function value across each of the different contour plots for easy visual comparison of the MAP objective landscapes. Suggestion: For values of sx and sy, you could use values around 0.25 and perhaps make them equal to each other. Note that your choice of these indicates how confident the prior is about the origin as the location.

Supplement your plots with a brief description of how your code works. Comment on the behavior of the MAP estimate of position (visually assessed from the contour plots; roughly center of the innermost contour) relative to the true position. Does the MAP estimate get closer to the true position as K increases? Doe is get more certain? Explain how your contours justify your conclusions.

Note: The additive Gaussian distributed noise used in this question is actually not appropriate, since it could lead to negatuve measurements, which are not legitimate for a proper distance sensor. However, in this question, we will ignore this issue and proceeding with this noise model for the sake of illustration. In practice, a multiplicative log-normal distributed noise may be more appropriate than an additive normal distributed noise.

Question 3 (20%)

Problem 2.13 from Duda-Hart-Stork textbook:
