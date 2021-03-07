Some thoughts on linear regression :

- the math behind it is pretty intuitive - this makes it a good introduction to the world of predictive models. 
  - with some calculus you can find a closed formula for finding coefficients in simple linear regression, which is pretty nice.  
- the linear in the name refers not to the shape of the model that you find (even though for simple cases it is often a line) but rather that the variables relate **linearly** to each other. 
  - This should definitely be more clear for beginners!!! ISLR does a good job of showing polynomials as valid models from linear regression.  



## Simple Linear Regression 

I really prefer the method of using `scipy.optimize.lsq_linear` for this task. You need to create a **Design Matrix**, defined [here](https://en.wikipedia.org/wiki/Design_matrix). This method lets you peek a little bit better under the hood (`polyfit` is cool but it does more work for you). 

For this task, you need to take formal uncertainties into account - so the steps to create such a matrix look like :

Step 1 : calculate sigma from data (sqrt of your response array) 

Step 2 : make an empty matrix with n rows and 2 columns. The number of columns grow whenever you add a higher degree term to your linear model. 

Step 3: populate the first column with your (predictor / sigma) and populate the second column with 1 / sigma. 

Then you simply plug the design matrix into the first argument of the `lsq_linear` function, and the second argument is your target vector. 

## Coming Up Soon...

I want to post some code walking you through every step in order to create and visualize a linear model using `scipy.optimize.lsq_linear`. It's one thing to talk about something, another thing to implement it from scratch. 