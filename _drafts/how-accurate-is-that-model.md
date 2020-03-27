---
layout: post
title: Verifying a linear model with R diagnostic plots
summary: R has built-in diagnostic plots to determine how well a model is fitting the data    
categories: [R, Linear Regression, Diagnostics]
mainimageurl: "/img/model-accuracy/poor-residuals-fitted.png"
mainimagealt: "Plot showing a model's Residuals vs Fitted values"
mainimageattribution: "Image from plotting a model in R"
codeexamples: "https://github.com/h-fuzzy-logic/R-Exploring-Generated-Data"
---

<h1 class="h4">Introduction</h1>
By fitting a linear regression model in R and then plotting the model, you can check to see how well the model is fitting the data.  Below is a code sample as a starting point:
```R
model <- lm(truth1 ~ dependency1 + dependency2)
plot(model)
```
Plotting the model will give diagnostics to uncover common problems such as assuming a linear relationship when it does not exist, having errors/residuals that are not normally distributed, having an irregular "scatter" to errors/residuals, or letting outliers heavily influence the model.  If individual data points are labeled with a number in the plot, the labelled points could be problematic.  The number label indicates the item in the data, so that it can be investigated more closely.  Below is more information the problem(s) each plot can uncover.  

<h1 class="h4">Plot - Residuals vs. Fitted</h1>
This plot can help detect if a non-linear relationship was overlooked.  If the model is a good fit, the plot will have no distinct patterns.
<div class="row mb-2 text-center">
	<div class="col-6">Model with Poor Fit
		<img src="{{ site.baseurl }}/img/model-accuracy/poor-residuals-fitted.png" class="img-fluid" alt="Residuals vs Fitted of poor model"/>
		<p><small class="text-muted"><cite title="Notice the clumping on the right">Notice the clumping on the right</cite></small></p>
	</div>
	<div class="col-6">Model with Good Fit
		<img src="{{ site.baseurl }}/img/model-accuracy/excellent-residuals-fitted.png" class="img-fluid" alt="Residuals vs Fitted of good model"/>
		<p><small class="text-muted"><cite title="Notice the straight line with no distinct patterns">Notice the straight line with no distinct patterns</cite></small></p>
	</div>
</div>

<h1 class="h4">Plot Details - Normal Q-Q</h1>
This plot verifies the distribution of the residuals.  If the model is a good fit, the plot will show normally distributed residuals which means the dots will mostly follow the straight dashed line.
<div class="row mb-2 text-center">
	<div class="col-6">Model with Poor Fit
		<img src="{{ site.baseurl }}/img/model-accuracy/poor-q-q.png" class="img-fluid" alt="Residuals vs Fitted of poor model"/>
		<p><small class="text-muted"><cite title="Notice that most of the values follow the dashed line since the data used was normally distributed">Notice that most of the values follow the dashed line since the data used was normally distributed</cite></small></p>
	</div>
	<div class="col-6">Model with Good Fit
		<img src="{{ site.baseurl }}/img/model-accuracy/excellent-q-q.png" class="img-fluid" alt="Residuals vs Fitted of good model"/>
		<p><small class="text-muted"><cite title="Notice that most of the values follow the dashed line and the dashed line stays close to zero.  This plot was created from a model that was nearly a perfect fit (because generated data was used)">Notice that most of the values follow the dashed line and the dashed line stays close to zero.  This plot was created from a model that was nearly a perfect fit (because generated data was used and the "truth" was known) </cite></small></p>
	</div>
</div>

<h1 class="h4">Plot Details - Scale-Location</h1>
This plot checks the variance of the residuals.  If the model is a good fit, the plot will show equally spread points when compared to the horizontal line.
<div class="row mb-2 text-center">
	<div class="col-6">Model with Poor Fit
		<img src="{{ site.baseurl }}/img/model-accuracy/poor-scale-location.png" class="img-fluid" alt="Residuals vs Fitted of poor model"/>
		<p><small class="text-muted"><cite title="Notice the clumping on the right">Notice the clumping on the right</cite></small></p>
	</div>
	<div class="col-6">Model with Good Fit
		<img src="{{ site.baseurl }}/img/model-accuracy/excellent-scale-location.png" class="img-fluid" alt="Residuals vs Fitted of good model"/>
		<p><small class="text-muted"><cite title="Notice when looking from left to right that the spacing stays consistent.">Notice when looking from left to right that the spacing stays consistent.</cite></small></p>
	</div>
</div>

<h1 class="h4">Plot Details - Residuals vs. Leverage</h1>
This plot uncovers influential cases (outliers).  If outliers are present, there will be a number next to the data point on the plot to indicate which item in the data is an outlier.  If outliers are detected, they may need to be removed so the analysis can be run again with out them.  For this plot, the patterns are not important.  It is important to look for values outside of the dashed lines (which shows Cooks Distance) and values that are in the right hand corners (upper and lower).
<div class="row mb-2 text-center">
	<div class="col-6">Model with Poor Fit
		<img src="{{ site.baseurl }}/img/model-accuracy/poor-residuals-leverage.png" class="img-fluid" alt="Residuals vs Fitted of poor model"/>
		<p><small class="text-muted"><cite title="Notice that data points 3, 6, and 18 need to be investigated more closely">Notice that data points 3, 6, and 18 need to be investigated more closely</cite></small></p>
	</div>
	<div class="col-6">Model with Good Fit
		<img src="{{ site.baseurl }}/img/model-accuracy/excellent-residuals-leverage.png" class="img-fluid" alt="Residuals vs Fitted of good model"/>
		<p><small class="text-muted"><cite title="Notice that data points 1, 2, and 811 need to be investigated more closely">Notice that the data points 1, 2, and 811 need to be investigated more closely</cite></small></p>
	</div>
</div>

<h1 class="h4">More information</h1>
Head over to <a href="{{ page.codeexamples }}" target="_blank"> GitHub</a> for code that explores these concepts with generated data, so that the "truth" is actually known when creating the models.  This approach makes it easier to understand the diagnostics because a "poor" model can be created and so can a "good/perfect" model.  