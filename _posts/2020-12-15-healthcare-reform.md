---
layout: post
title:  Who supports Medicare for All? 
date:   2020-12-15 18:35:00 +0000
categories: class, voting, social cleavage, ideology
---

Universal healthcare coverage has been the Democratic party's white whale for decades. FDR had to remove national health insurance from the Social Security Act in 1935 due to opposition from the American Medical Association, Truman failed to get national health insurance past a conservative congress, the best Johnson could do after a landslide election victory in 1964 was get Medicare for the elderly and Medicaid for the poor, and various attempts at universal coverage failed throughout the 1970s and 1990s.

Democrats finally did succeed in passing healthcare reform in the second year of the Obama administration. The Affordable Care Act (ACA), commonly referred to as Obamacare, worked by expanding Medicaid to cover more people with low incomes, creating individual insurance exchanges where people can purchase health insurance plans from private insurers, providing people buying insurance on the exchanges with an income-based subsidy to cover the cost, mandating that everyone buy health insurance, banning insurance companies from discriminating against people with pre-existing conditions, and allowing young people to stay on their parents' plans until they turn 26. Over the last 10 years, the ACA has gained enemies from both the left (who argue it didn't go far enough) and the right (who object to the tax increases and new regulations). 

It is well-known that opposition to 'Obamacare' has been a rallying cry for conservative Republicans, especially the Tea Party and House Freedom Caucus, since it was signed into law in 2010. The ACA's unpopularity was probably one of the main reasons that Republicans were able to retake the House in 2010; it certainly contributed to the sheer size of their victory. Since then, opinions on the ACA have been closely tied to opinions of President Obama. Similarly, 'repeal and replace' became a key component of Republican campaigns after 2010. It was one of the two items at the top of the agenda when the GOP held the House, Senate, and Oval Office after 2016 &mdash; even if by then its popularity had recovered and Republicans failed to do anything more than *de facto* eliminate the individual mandate.

Medicare for All (M4A), the moniker for a variety of different proposals for extending Medicare to the whole population and create a single payer healthcare system, does not have the same connection with the Obama administration or the Tea Party. While a great deal of attention has been paid to different M4A proposals since Bernie Sanders campaigned on it in the 2016 Democratic primary, there hasn't been much work aiming to understand the demographic basis of support for it (and how it compares to that of the ACA).

Today I set out to remedy that. The Kaiser Family Foundation has been regularly conducting polling on whether people support the ACA and M4A for years now and I was able to get access to the polls where both questions were asked in 2020 via Cornell University's Roper Center for Public Opinion Research. The individual response data contains information on income, race, education, age, sex, and state of residence. Using a method called multi-level regression with post-stratification, I estimated models of individual support for the ACA and M4A using these individual characteristics and various state-level predictors (median household income, share with a bachelor's degree or higher, and Joe Biden's share of the popular vote in the 2020 presidential election) &mdash; this is the 'multi-level regression' part. I then used this model in conjuction with data I compiled from the 2019 American Community Survey showing what percent of a state's population came from each demographic group to predict levels of support by state and individual characteristic &mdash; this is the post-stratification part.

The models for Medicare for All and Obamacare ended up being slightly different because I needed to drop random effects with extremely low variance to aid in convergence in both cases.

The code for the M4A model using the `lme4` package in R is: `glmer(m4a.support ~ (1|sex) + (1|age) + (1|educ) + (1|race) + (1|income) + (1|race:educ) + (1|income:race) + (1|income:region) + (1|race:region) + log(median_income) + degree + dem20,df,family=binomial)`

The ACA model is: `glmer(aca.support ~ (1|sex) + (1|age) + (1|educ) + (1|race) + (1|income) + (1|race:educ) + (1|income:race) + (1|income:educ) + (1|race:region) + log(median_income) + degree + dem20,df,family=binomial)`

I have created a series of maps that indicate support for the Affordable Care Act and Medicare for All by state. The first set looks at race and education, the second looks at income and education. I chose these because they highlight a very interesting difference in who supports each policy (sorry about the size of the images, they are pretty high definition so I suggest opening in another tab and zooming in). 

<img src="{{site.baseurl}}/assets/img/aca_race_education.png" alt="Support for the ACA by race and education" style="zoom:50%;" />

Opinions on the ACA seem to be divided in the same way national politics has become divided &mdash; highly educated voters of all incomes and races tend to support it, minorities are much more likely to support it than white people, and higher income modestly reduces support for it. 

<img src="{{site.baseurl}}/assets/img/aca_income_education.png" alt="Support for the ACA by income and education" style="zoom:50%;" />

M4A, however, doesn't seem to have been affected by the same polarisation (the first indication of this was when the income by education interaction effect had a variance very close to zero when I first fit the model).

<img src="{{site.baseurl}}/assets/img/m4a_income_education.png" alt="Support for M4A by income and education" style="zoom:50%;" />

Conditional on income, more educated people are *less* likely to support it. Meanwhile, income is just as if not more predictive of support for Medicare for All and race is slightly less so (though this may be in part because Black people tend to link their support for President Obama with support for his signature legislative achievement).

<img src="{{site.baseurl}}/assets/img/m4a_race_education.png" alt="Support for M4A by race and education" style="zoom:50%;" />

Before I move on to my conclusions from this analysis, I want to point out that both the ACA and Medicare for All are now popular; my models estimate that overall support for each policy is nearly identical at 53%. This suggests that Democrat's running on M4a is not the electoral suicide that some moderates think it would be. In fact, people in red states are often more likely to say they favour Medicare for All than they are to say the same for the Affordable Care Act.

<img src="{{site.baseurl}}/assets/img/aca_state.png" alt="Support for the ACA by state" style="zoom:50%;" />

<img src="{{site.baseurl}}/assets/img/m4a_state.png" alt="Support for the ACA by state" style="zoom:50%;" />

My conclusions from this to a certain extent reflect my existing convictions that the Democratic party should go back to its New Deal roots and be a lot more like Harry Truman and Hubert Humphrey than Bill Clinton and Joe Biden, but at least on this issue it is clear that the public supports a large expansion of Medicare to cover many more people. Of course, the devil is in the details. And I don't doubt that there would be strong opposition both from Republicans (there won't be any bipartisan national health insurance bills like in the 1970s) and from insurance companies. But this is a chance for the Democratic party to attach themselves firmly to economic populism that is, well, popular and disarm Republican attacks that take advantage of the complexity of policies like the ACA. 

In the weeks to come I hope to show similar patterns for other policies, like raising the minimum wage and making public universities tuition free, that are not only popular overall but also popular among groups that Democrats need to at least not lose too badly to the Republicans with (i.e. White voters without a college degree). This is especially true in light of the 2016 election results proving that the ['coalition of the ascendant'](https://cdn.americanprogress.org/wp-content/uploads/2012/12/ObamaCoalition-5.pdf) is not bound to win and the 2020 election results proving that demography is indeed not destiny.