# BerkeleyPractical_II
Practical Application II
<img src='images/kurt.jpeg'>
<h1> Welcome to Daniel's Practical Application II</h1>
<br><br>
<p>In this application, I explored the used car dataset from Kaggle that contained information on more than 3 million used cars. My goal was to understand what factors make cars more or less expensive. As a result of my analysis, I will provide you with a clear recommendation as to what consumers value in used cars. Lets dive in!</p>

<h3>
  Let's have our look at the CRISP-DM Framework. 
  </h3>
<p>The CRISP-DM Framework is designed to maximize outcomes for a desired deployment and to help wrap technical techniques into best business objectives by using iterative and (somestimes) circular process flow. To attain such best business outcomes, one must first understand the business. Our client wants to know what do consumers value most in used cars. This is obviously to drive sales at their business as well as give consumers the best offering, because after all, it is what they desire. Next, as an AI/ML engineer, one must understand the data clearly. Without clear understanding for the data, one can not begin to prepare the data for modeling, which is our next step. Modeling will yeild best features (details) about the data that affect the targeted variable (in this case, pricing). In addition, modeling will also help suggest which algorithm is best for the use case, by utilizing scoring mechanisms.  Further, we can move to evaluation of what we have done thus far. We can glean from the results that have been rendered. This process can be circular to ensure best outcome for our client and their business goals.</p>
<h3>Data Understanding</h3>
<p><img src='https://awesomescreenshot.s3.amazonaws.com/image/3446742/30457823-0d8ff7cccfd3d438c196b6953e8db1da.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAJSCJQ2NM3XLFPVKA%2F20220721%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20220721T164254Z&X-Amz-Expires=28800&X-Amz-SignedHeaders=host&X-Amz-Signature=aee6837d253d4b9dadd5286f1509f3e991b2440f1cdb8c2530dc7d58805f78b2'><br><br> In our dataset, we can see various features, which we will work with. Some are swiftly identifiable as important/unimportant and others are not as easily to swiftly identify. For example, we can get rid of VIN number, State, Region, ID, as these wont have bearing on the favorability of the vehicle. We do initially see that there are some blank field in our dataset. We'll have a look into how we can best make decision of working with this. We may need to drop/discard it.
</p>
<h3>Insights on Data Understanding</h3>
<p>We're able to gain meaningful insights from viewing our dataset. Let's take note of some important attributes (jupiter notebook of sourcing may be found here :<br>

&bull;The latest model year is 2022 and the oldest is 1900. And we have the most of 2017 model year in inventory.<br>
&bull;There are 209 12-cylinder vehicles<br>
&bull;There are 1455 10-cylinder vehicles<br>
&bull;There are 72062 8-cylinder vehicles<br>
&bull;There are 94,169 6-cylinder vehicles<br>
&bull;There are 1712 5-cylinder vehicles<br>
&bull;There are 77,642 4-cylinder vehicles<br>
&bull;There are 655 3-cylinder vehicles<br>
&bull;From the dataset, there are 5 known types of fuel compatibilities: gas, diesel, hybrid, electric, other<br>
&bull;From the dataset, we have vehicle mileage ranging from 0 miles to 1 to 10,000,000 (prior to dataset being cleaned)<br>
&bull;Title status' range from: clean, rebuilt, salvage, lien, missing, parts only<br>
&bull;Transmission types include: automatic, manual and other.<br>
&bull;There are 131,904 4-wheel drive vehicles; 105517 front-wheel drive vehicles, and 58892 rear-wheel drive vehicles<br>
&bull;Car types include: Sedan, SUV, Pickup, Truck, Coupe, Hatchback, Wagon, Van, Convertible, Mini-Van, OffRoad, Bus, and other.<br>
&bull;Vehicles are sources from all 50 states and the Dictrict of Columbia (Washington DC).<br>
&bull;California has the most of vehicles at 50,614<br>
&bull;North Dakota has the fewest of vehicles at 410<br>

</p>
<h3>Data Preparation</h3>
<p>
&bull;I chose to leave manufacturer with NaN as we may later be able to identify the vehicles based on the model<br>
&bull;I close to omit VIN, ID because we will later drop it<br>
&bull;Upon examination, we can see the following columns are non essential and will have no influence as they are attributes: id, vin<br>
&bull;Thus, lets drop those columns, then drop duplicates<br>
&bull;Lets check for anomolies in price. we need to manually check to make sure the model is not going to get thrown off by non-realistic pricing data<br>
&bull;This could also mean poising in some cases<br>
&bull;There outliers where the pricing just does not make sense. For example, the 2007 toyota tundra that costs $3,736,928,711 and the 1996 GMC Sierra pickup truck that cost 123,456,789.<br>
&bull;These are just not practical, so we need to drop them with the goal of not adversely our predictions.<br>
&bull;Im not sure that I like the word 'cylinders' on the values in the cylinders column. so lets strip it change from float to int<br>
&bull;Same thing where we have string values for transmission types. Lets convert these to int. Could have also used label encoder.<br>
&bull;Same thing for drive type -- i want this as numerical value. of type int.<br>
&bull;We have a problem where we need to figure out how to get car condition where there is a nan value.<br>
&bull;My guess is that we can take the price of the car and figure out what the possible condition might be<br>
&bull;It may be a bit off due to different makes of cars having different values, but it will be an earnest try<br>
&bull;Same logic applies for trying to figure out title status where it is nan<br>
   
</p>
<h3>Modeling</h3>
<p></p>
<h3>Evaluationg</h3>
<p>With some modeling accomplished, I reflect on what we identify as a high quality model and what we are able to learn from this. I've reviewed our business objective and exploree how well I can provide meaningful insight on drivers of used car prices. My goal now is to distill your findings and determine whether the earlier phases need revisitation and adjustment or if you have information of value to bring back to your client.<br><br>
<b>Let's take a recap of our models and what we may be receiving from each:</b><br>
  <b><u>Linear regression</b></u><br>
is been studied at great length, and there is a lot of literature on how your data must be structured to make best use of the model.<br>

As such, there is a lot of sophistication when talking about these requirements and expectations which can be intimidating. In practice, you can uses these rules more as rules of thumb when using Ordinary Least Squares Regression, the most common implementation of linear regression.<br>

Try different preparations of your data using these heuristics and see what works best for your problem.<br>

&bull;Linear Assumption. Linear regression assumes that the relationship between your input and output is linear. It does not support anything else. This may be obvious, but it is good to remember when you have a lot of attributes. You may need to transform data to make the relationship linear (e.g. log transform for an exponential relationship).<br>

&bull;Remove Noise. Linear regression assumes that your input and output variables are not noisy. Consider using data cleaning operations that let you better expose and clarify the signal in your data. This is most important for the output variable and you want to remove outliers in the output variable (y) if possible.<br>

&bull;Remove Collinearity. Linear regression will over-fit your data when you have highly correlated input variables. Consider calculating pairwise correlations for your input data and removing the most correlated.<br>

&bull;Gaussian Distributions. Linear regression will make more reliable predictions if your input and output variables have a Gaussian distribution. You may get some benefit using transforms (e.g. log or BoxCox) on you variables to make their distribution more Gaussian looking.<br>

&bull;Rescale Inputs: Linear regression will often make more reliable predictions if you rescale input variables using standardization or normalization.<br><br>

<b><u>Ridge Regression</b></u>
Ridge regression addresses some of the problems of Ordinary Least Squares by imposing a penalty on the size of coefficients. The ridge coefficients minimize a penalized residual sum of squares,


α>=0 is a complexity parameter that controls the amount of shrinkage: the larger the value of α , the greater the amount of shrinkage and thus the coefficients become more robust to collinearity.<br>

Ridge regression is an L2 penalized model. Add the squared sum of the weights to the least-squares cost function.<br>

<b><u>Lasso Regression</b></u>
A linear model that estimates sparse coefficients.<br>

Mathematically, it consists of a linear model trained with ℓ1 prior as regularizer. The objective function to minimize is:<br>


The lasso estimate thus solves the minimization of the least-squares penalty with α∣∣∣∣w∣∣∣∣1 added, where α is a constant and ∣∣∣∣w∣∣∣∣1 is the ℓ1−norm of the parameter vector.

Out of our models, we can see it favors "transmission" as a key feature as it is showing highest importance and has heavy influence on price.

When reviewing R2 Score we can see our highest performer was KNN.
KNN also held the lowest RMSE followed by Ridge, Lasso, then Linear.
KNN also held the lowest MSE followed by Ridge, Lasso, then Linear.


</p>
<h3>Deployment</h3>
<p>Now that we've settled on our models and findings, it is time to deliver the information to the client. You should organize your work as a basic report that details your primary findings. Keep in mind that your audience is a group of used car dealers interested in fine tuning their inventory.

<i>From our findings we can know that:<i>

&bull;Use of KNN will yield best scoring for price predictions<br>
&bull;Most important feature is transmission, followed by the number of cylinders, then the year of the vehicle, and drive type.<br>
&bull;Used car dealers should use this valuable information when determining what types of cars to bring onto their lot for resale. It could likely influence how much volume they are moving per period as well as be a sure way to lure customers in.
&bull;With regard to transmission type, we can see that type of Automatic is preferred, closely followed by Manual<br>
&bull;Regarding the number of cylinders, best interest is drawn by consumers who prefer 8 cylinder vehicles!<br>
&bull;The sweet spot for the year of the vehicle appears to be between 2013 and 2018.<br>
&bull;The most preferred vehicle types by consumers is: SUV, Sedan, and Truck</p>
