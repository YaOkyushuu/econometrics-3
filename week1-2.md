#Econometrics III
-----
(菅史彦.　九州大学　2019)　

***WEEK 1***

1. Nonexperimental data

   observational data, or social science data.

2. Data type

   - cross-sectional data **横截面数据**
     - sample of different individuals ,<mark>at a given point of time</mark>
     - often ignore minor time differences
     - observations are more or less independent
     - *applied microeconomics*
   - time series data **时间序列数据**
     - one variable(or several variables) <mark>over time </mark>
     - ![timeseries data](C:\Users\Administrator\Desktop\unnamed-chunk-9-1.png)
     - <mark>serially correlated</mark>. trends and seasonality.
     - *applied macroeconomics and finance*
   - pooled cross sections **混合截面数据**
     - two or more cross sections combined
     - evaluate policy changes
   - panel/longitudinal data **面板数据**
     - same cross sections followed over time = *time series+cross sections*
     - can be used to account for time-invariant un-observables: eg. lags in decision making; city crime statistics ‘s un-observable city characteristics

3. r regression (SLR)

   ```R
   #install Wooldridge package to use datasets
   data("crime")
   result <- lm(wage ~ educ+exper+training, data = crime)
   summary(result)
   ```

4. definition of <u>causal effect</u>: ***ceteris paribus***

   <mark>how does *y* change if variable *x* is changed, but all other relevant factors are held constant?</mark>

5. topics

   - OLS

   - IV

   - Fixed Effect & Random Effect Model

   - MLE

   - Probit/Logit

   - Tobit

   - Heckman Two Step

***WEEK 2***

1. SLR --- *Simple Linear Regression*

   Focus: <mark>when is there a causal interpretion?</mark>

   Assumptions:

   1. Conditional Expectation independence

      $E(u|x)=0$ (which <u>is a function of $x$</u>)

      $x$ does not contain any information about mean of $u$.

      - PRF *Population Regression Function*

   $$
   \begin{aligned}
   E(y|x)&=E(\beta_0+\beta_1x+u|x)\\
   &=\beta_0+\beta_1x+E(u|x)\\
   &=\beta_0+\beta_1x\\
   \end{aligned}
   $$
   
   ![slr](C:\Users\Administrator\Desktop\SLR.png)
   $$
   
   $$
   
   
   - Sample analogue
   
     - regression residuals
       $$
       \hat{u}=y^i-\hat{y_i}
       $$
       minimize sum of squared residuals:
       $$
       min\Sigma\hat{u_i}^2 \to \hat{\beta_0},\hat{\beta_1}
       $$
   
   - OLS estimates *Ordinary Least Squares Estimates*
   
     by minimizing SSR, we estimates $\beta_0$ and $\beta_1$.
   
     
   
   - error terms
   
     fitted regression line - <mark>unknown population regression line.</mark>
   
     <u>differ from residuals</u>
   
   
   
   2. R introduction
   
      ```R
      data("gpa1")
      #subset dataset gpa1, we only use 3 columns
      gpa1small <- gpa1[,c("colGPA","hsGPA","ACT")]
      summary(gpa1small)
      #variation and correlation index(pearson)
      var(gpa1small)
      cor(gpa1small)
      #standard deviation
      sd(gpa1small$ACT)
      #histogram
      hist(gpa1small$colGPA)
      #scatter plots 
      plot(gpa1small$colGPA,gpa1small$hsGPA)
      #rgl package
      install.package("rgl")
      library("rgl")
      plot3d(gpa1small$colGPA,gpa1small$hsGPA)# this function must contain 3 vars.
      #linear regression model
      result <- lm(gpa1small$colGPA~gpa1small$hsGPA+gpa1small$ACT) 
      result <- lm(colGPA~hsGPA+ACT,data=gpa1small) 
      summary(result)
      #obtain bata1 by coefficients index
      beta1<-result$coefficients[2]
      ```
   
      
   
   
   
   



