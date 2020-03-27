---
layout: post
title: Verifying a linear model with R diagnostic plots
summary: R has bulit-in diagnostic plots check to see how well the model is fitting the data    
categories: [R, Logistic Regression, Diagnostics]
mainimageurl: "/img/2019-12-02-customizing-css-for-jupyter-notebooks-1.png"
mainimagealt: "Diagnostics"
codeexamples: "https://github.com/h-fuzzy-logic/Python-Exploring-User-Generated-Events/blob/master/Exploring%20User%20Generated%20Events.ipynb"
---

<h1 class="h4">Introduction</h1>
By fitting a logistic regression model in R and then plotting the model, you can check to see how well the model is fitting the data.  Below is a code sample as a starting point:
```R
model <- lm(truth1 ~ dependency1 + dependency2)
plot(model)
```
Plotting the model will give diagnostics to uncover common problems such as assuming a linear relationship when it does not exist, having errors/residuals that are not normally distributed, having an irregular "scatter" to errors/residuals, or letting outliers heavily influence the model.  Below is more information about how to recognize each problem.  

<h1 class="h4">Plot - Residuals vs. Fitted</h1>
This plot can help detect if a non-linear relationship was overlooked.  If the model is a good fit, the plot will have no distinct patterns.
<div class="row mb-2">
	<div class="col-6">test</div>
	<div class="col-6">test</div>
</div>

<h1 class="h4">Plot Details - Normal Q-Q</h1>
This plot verifies the distribution of the residiuals.  Expecting normally distributed residuals if the model is a good fit.
<div class="row mb-2">
	<div class="col-6">test</div>
	<div class="col-6">test</div>
</div>

<h1 class="h4">Plot Details - Scale-Location</h1>
checks the variance of the residuals.  Expecting equally spread points if the model is a good fit.
<div class="row mb-2">
	<div class="col-6">test</div>
	<div class="col-6">test</div>
</div>

<h1 class="h4">Plot Details - SResiduals vs. Leverage</h1>
uncovers influential cases (outliers).  If outliers are detected, they may need to be removed so the anaylsis can be run again with out them.
<div class="row mb-2">
	<div class="col-6">test</div>
	<div class="col-6">test</div>
</div>

<h1 class="h4">More information</h1>
For more code samples, check out 
