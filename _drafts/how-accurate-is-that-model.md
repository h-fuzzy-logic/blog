---
layout: post
title: R diagnostics for a linear model
summary: R has bulit-in diagnostic plots check to see how well the model is fitting the data    
categories: [R, Logistic Regression, Diagnostics]
mainimageurl: "/img/2019-12-02-customizing-css-for-jupyter-notebooks-1.png"
mainimagealt: "Diagnostics"
---

<h1 class="h4">Introduction</h1>
By fitting a logistic regression model and plotting the model, you can check to see how well the model is fitting the data.  Below is a code sample as a starting point:
```R
model <- lm(truth1 ~ dependency1 + dependency2)
plot(model)
```

<h1 class="h4">Resulting diagnostics from plotting the model</h1>
<ol>
	<li><b>Residuals vs. Fitted</b> can help detect if a non-linear relationship was overlooked.  Expecting no distinct patterns if the model is a good fit.</li>
	<li><b>Normal Q-Q</b> verifies the distribution of the residiuals.  Expecting normally distributed residuals if the model is a good fit.</li>
	<li><b>Scale-Location</b> checks the variance of the residuals.  Expecting equally spread points if the model is a good fit. </li>
	<li><b>Residuals vs. Leverage</b> uncovers influential cases (outliers).  If outliers are detected, they may need to be removed so the anaylsis can be run again with out them.</li>
</ol>



<h1 class="h4">More information</h1>
For more code samples, check out 
