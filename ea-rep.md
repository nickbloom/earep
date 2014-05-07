---
title: "Replicating Embedded Altruism: Blood Collection Regimes and the European Union’s Donor Population"
author:
- name: Nick Bloom
  affiliation: Duke University
date: April 21, 2014
...

### Embedded Altruism: Blood Collection Regimes and the European Union’s Donor Population

Kieran Healy's original paper investigated the role of organizations in the collection of blood in European countries. At the time, colloquial and scholarly opinions of blood donation were in agreement that blood donation was a "perfect example" of individual altruism. Healy's article challenged this sentiment in two ways. 

First, he compiles expectations from the literature to construct a 'modal donor' as a series of hypotheses. He then shows that this 'modal donor' is *not* the most likely individual to donate blood across European countries.

Second, he demonstrates the institutional effects of collection regimes by interacting individual-level characteristics with the collection regimes. He finds both variation in the modal donor profile by collection regime, and significant effects of the collection regimes themselves.

### Data and Coding

The data come from the Eurobarometer Survey, an annual survey of several European Union countries. For my reanalysis, I use variables from Eurobarometer 41.0, collected in 1994, which included several questions about blood and plasma donation, as well as standard demographic questions. The analyses include all of the Eurobarometer countries except for Finland, whose respondents were missing on all the blood donation variables.

#### Dependent Variables

For the individual-level pooled within-country regressions, the dependent variable measures whether the respondent had given blood in the last year. For the multilevel regression, the dependent variable measures whether the respondent had ever given blood.

#### Independent Variables

As in Healy [-@Healy:2000ev], variables are coded with the modal donor as the reference. *Age* is centered on 35-year-olds. *Years of Education* is centered on those with 16 years of education, roughly college-educated individuals. *Church attendance* is coded on a five-point scale from `0` for 'never attends' to `4` for 'attends weekly'. *Income* is measured on a Eurobarometer scale from 0-12, which standardizes income across the currencies of the various countries. *Sex* is a dichotomous measure for Female.

*Network* is a four-level scale measuring the number of ties a respondent has to a blood transfusion recipient; `0` is ties to no one, whereas `3` is ties to self, friend/family, and someone else who has received a transfusion.

*Collection Regime* is included in the multilevel regression as a dichotomous variable for each of the regimes, according to the coding in Healy [-@Healy:2000ev].

### Original Methods

Healy uses binary logit model for the within-country analysis, and a multilevel/mixed-effects logit model for the institutional-level analysis. The equation for the multilevel model is as follows:

$log \left(\frac{p_{ij}}{1-p_{ij}}\right) = \beta_{0j} + \beta_{ij} * X_{ij} + \beta_{j} * X_{j}+ \upsilon_{j} + \epsilon_{ij}$

where $p$ is the probability of giving blood for an individual in the sample (the lefthand side of the equation converts this probability to log odds). $\beta_{0j}$ is a country-level random intercept with error term $\upsilon_{j}, $\beta_{ij}$ is a vector of individual-level predictors for variable vector $X_{ij}$, and $\beta_{j}$ is a vector of country-level predictors for variable vector $X_{j}$.

### Original Results

I report tables and results from Healy [-@Healy:W-AGZX5C], which are corrected versions of the tables in Healy [-@Healy:2000ev]. In the within-country regressions, Healy finds that men are more likely to donate that women in every country (except Belgium, whose coefficient for Female is not statistically significant). He also finds that individuals are almost universally less likely to donate after age 35.

He finds little support for the influence of educational attainment and income on recent donation; education only singificantly increases the odds of donating blood in three of the countries (France, Norway, and Greece), and is negative (but not significant) in five of the countries. Income is only positive and significant in four of the countries (Belgium, Netherlands, Denmark, and Norway), and two of those four are significant at p<0.1. However, he finds significant effects when changing the dependent variable to *ever* giving blood.

Healy finds little support for the hypothesis that a respondent's network of transfusion recipients increases that respondent's odds of donating, with statistically significant, positive coefficients in only three countries. Finally, he finds that religious attendance is statistically significant in two of the countries with Red Cross collection regimes, which indicates that the Red Cross may target religious congregations as donors. 

### Replication

Thanks to a coding memo generously supplied by Healy himself, I was able to produce near-identical results to those he found. Whereas Healy used `glmmPQL`, a Quasi-Likelihood approximation for his multilevel estimation, I use the more recently-developed `lme4` package in R, which estimates multilevel GLMs using Gauss-Hermite Quadrature maximum likelihood estimation. This results in two minor differences between the results. First, some coefficients are discrepant due to rounding differences at the fourth decimal place - coefficient differences are, at most, 0.001. Second, `lme4` provides z-scores rather than t-scores for coefficients.

Finally, rather than report t-values for coefficients, I report their standard errors in both tables. Tables with t-values are available upon request.


### Extension

To extend the analysis in Healy [-@Healy:2000ev], I estimate all models as linear probability models. Linear probability models (LPM) estimate binomial outcomes using OLS. The advantage of LPMs over logit models is that the coefficients for LPMs are the change in probability for a one-unit change in the independent variable, whereas coefficients for logit regressions are the change in log-odds for a one-unit change in the independent variable.

In addition, I provide more robust estimates for both the linear and logit multilevel models, by presenting results from a 1000-iteration bootstrap of each.

The motivation for these extensions are twofold. First, computing power has increased dramatically in the intervening decade since the article's initial publication, as have packages for more robust estimation. Second, linear probability models are often touted as robust, quick alternatives to logistic models, that produce adequately accurate results.

### Results




### Discussion


#### Code

```{r, message=FALSE, error=FALSE, results='asis'}
y<-(c(seq(1:12),14))
for (g in y){
  groupname<-paste('group',g,sep="")
  groups<-assign(groupname, subset(eurobar2, country==g), envir = .GlobalEnv)
  lmname<-paste('lm',g,sep="")
  assign(lmname, lm(lastyr ~ female + agecent + educcent + income + network + attend, data=groups))
}

system.time(mlm.2<-lmer(evdon ~ female + agecent + educcent + income + network + attend + I(female*redcross) + I(agecent*redcross) + I(educcent*redcross) + I(income*redcross) + I(network*redcross) + I(attend*redcross) + I(female*banking) + I(agecent*banking) + I(educcent*banking) + I(income*banking) + I(network*banking) + I(attend*banking)+ I(female*dongroup) + I(agecent*dongroup) + I(educcent*dongroup) + I(income*dongroup) + I(network*dongroup) + I(attend*dongroup) +  redcross + banking + dongroup + (1|country), data=eurobar))
stargazer(mlm.2, type='html',style='ajs')
```






# References
\setlength{\parindent}{-0.2in}
\setlength{\leftskip}{0.2in}
\setlength{\parskip}{8pt}
\vspace*{-0.2in}
\noindent