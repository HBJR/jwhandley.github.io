---
layout: post
title:  The working class and the Democratic party
date:   2020-12-12 13:48:00 +0000
categories: class, voting, social cleavage, ideology
---

One of the dominant narratives of the 2016 presidential election was the unusually high level of support that Donald Trump got from white voters without a university degree &mdash; the so-called 'white working class'. This led to a wave of research focusing on how the polls underestimated the white working class share of the electorate[^1], the demography and views of 2012-2016 vote switchers[^2], and the voting patterns of the white working class writ large.[^3] The wave of attention on the preferences and electoral behaviour of the white working class was particularly salient because of the consensus that failing to ensure a high enough share of non-college educated white voters in polling samples led to the polling misses in Wisconsin, Michigan, and Pennsylvania &mdash; three state that ended up being decisive for Trump's victory.[^4]

While there is plenty of disagreement on the narrative that Trump was able to peel working class white voters away from the Democratic party (in fact one of the papers I linked above argues that the trend long predates Trump), I don't intend to dispute that here. It is clear that white voters without a college degree are the demographic group most supportive of Donald Trump and indeed that at least a plurality of them have voted for Republican candidates for President for a long time. Using data from the American National Election Studies, we can see that the white non-college two-party Democratic vote share for President has been below 50% since the 2000 election. Indeed, the last time white voters without a college degree were at least as likely to support the Democrat than the entire electorate was in 1964.

Democratic two-party presidential vote share:

Year | Whites without a degree | All voters
:--  | :---------------------: | ---------:
1952 | 41%                     | 42%
1956 | 40%                     | 40%
1960 | 49%                     | 49%
1964 | 67%                     | 67%
1968 | 43%                     | 46%
1972 | 29%                     | 36%
1976 | 49%                     | 51%
1980 | 37%                     | 44%
1984 | 34%                     | 42%
1988 | 39%                     | 47%
1992 | 55%                     | 59%  
1996 | 53%                     | 58%
2000 | 45%                     | 52%
2004 | 40%                     | 49%
2008 | 44%                     | 55%
2012 | 40%                     | 54%
2016 | 34%                     | 53%


Source: American National Election Study (1952-2016); my calculations

What I have a problem with is that 'working class' and 'doesn't have a college degree' are so often conflated in the popular discourse around this. Supporters of this definition of working class rightly argue that education is closely linked with social standing and earning potential &mdash; both of which are deeply grounded in the popular Weberian conception of class as consisting of wealth, prestige, and power. The issue is that education is merely a proxy for this things and we need more than a priori reasoning to tell us that high support among the less educated automatically means high support among those with low wealth and income or with low prestige and power. At the very least, we should look at income as a more direct indication of both immediate material deprivation and because it actually provides a better indicator of lifetime earning potential that other measures of class.[^5]

Another problem with the focus on the 'white working class' in the aftermath of the 2016 election is that it ignores the views of working class people of colour, who overwhelmingly did and do not support President Trump (despite small swings among Black and Latino voters in the 2020 election[^6]). In some ways, there is something to the argument that the class divide is only relevant for white voters; since the 1960s race has been the dominant political cleavage in the US, to the extent that Republican support from Black voters tends to stay in the single digits.[^7] However, it is impossible to ignore the history of racism in the United States and how this has created persistent economic divides between racial groups. People of colour are disproportionately working class in the US, and their preferences and voting patterns matter as much for the American class cleavage as those of working class whites do.

Because of these factors, I want to look at how voting patterns have changed (or if they have changed) according to class (as measured by both income and education levels, including both white and non-white voters) over time. To do this I am using two main data sources. First, the American National Election Studies have individual response data on income, education, and voting going all the way back to the 1952 presidential election. This gives the broadest picture of long term trends in class voting. Second, the Cooperative Congressional Election Study &mdash; which has been running since 2006 &mdash; has a larger sample size which allows me to go into more detail on both education and income. It also has responses from the 2018 midterms, so it gives an early indication of whether the changes in the 2016 presidential election will be durable.

Inspired by work on multilevel regression and post-stratification,[^8] I decided to estimate regression models with random intercepts for different categories of income, education, the interaction between income and education, the interaction between each of these variables and the election year, and the election year in order to deal with the problem of relatively small samples of individual who, e.g., have less than a high school education but have incomes over $100,000 a year. This relies on partial pooling towards the mean, where we essentially assume that voters with similar characteristics vote similarly to each other. I used the `lme4` package in R to estimate these models and then used the models to make predictions for each level of income and education for each year.

<img src="{{site.baseurl}}/assets/img/income_education_vote_anes.png" alt="Presidential vote share by income and education" style="zoom:25%;" />

This shows some interesting patterns that go against some of the conventional wisdom around class voting. Aside from the top 5%, voters were relatively unpolarised along income lines in the 1950s and 1960s, with marked increases in the income cleavage during the 1970s and 1980s. This goes against the popular idea of the 'Reagan Democrat' reflecting strong working class support for Ronald Reagan. The fact of the matter is that Reagan's policies disporportionately harmed low income voters and they returned the favour by supporting him at much lower rates than rich voters did. Income was also a particularly strong predictor of vote choice in the 2008 election. This is hardly surprising given the context of the worst financial crisis since the Great Depression. Even so, income voting was not especially weak in any of the elections between 1988 and 2012. Based on this measure, the class cleavage in American politics has *grown* over the last few decades.

At least that was until the 2016 election. This was the first time since the 1960s that income had almost no impact of vote choice. This partially serves to explain why pollsters failed to control for education in 2016; it hadn't had a huge or consistent effect on vote choice in past elections. If you look closely, you might notice that voters with degrees have at times been more likely than those without to vote for the Democratic candidate and at times been less likely. Voters with degrees were more likely to support the Democrat than those with only high school diplomas or less in 1972, 1984, 2000, 2004, and 2016. They were more likely to support the Democrat than those with some college in 1968 and 2008 as well. I will get to this more in a later section, but I think the common factor between most of these elections is a high salience of social rather than economic issues in the campaign. In 1968 and 1972, it was Vietnam. In 2004 and 2008, it was Iraq. In 2016, Donald Trump made political correctness, racism, sexism, and xenophobia key aspects of his campaign (and vote switchers to him from 2012 tended to score much higher on indices of sexism and racial resentment than other voters[^2]). 

Before examining this point in more detail, I want to zoom in on recent elections by looking at the results of a similar analysis of Cooperative Congressional Election Study data.

<img src="{{site.baseurl}}/assets/img/income_educ_vote_cces.png" alt="House of Representatives vote share by income and education" style="zoom:25%;" />

The CCES data looks very similar to the ANES data, which is a good sign for the validity of my approach. Importantly, it also shows us how people voted in midterm elections so we have more cases to look at. Education was strongly predictive of vote choice in the 2010 and 2014 midterms, giving a hint of what was to come in 2016. This makes sense given the outsized role that the Tea Party played in the 2010 midterms. The 2014 midterms are a little more ambiguous, but given how polarised support for repealing the Affordable Care Act (Obamacare) is along education lines, it is possible that low education voters were motivated to vote for Republicans to oppose the President's healthcare policies.

Repeal Obamacare | High school or less | Some college | Degree
:--------------- | :-----------------: | :----------: | -----:
Support          | 50.3%               | 44.2%        | 36.3%
Oppose           | 49.7%               | 55.8%        | 63.7%

Source: CCES 2018; my calculations

The 2018 midterms give an indication of what I think will be the 'new normal' for class voting in US elections. The education divide stayed as big as ever, but low income voters became more likely to vote for Democrats than in 2016. Exit polls from the 2020 presidential election suggest that this pattern has largely held. AP Votecast data suggest that Biden won voters with incomes less than $50,000 by 8 points and National Election Pool data say he won by that group by 11 points. Both sources have Biden winning college graduates by double digits and losing among those without degrees in the low single digits.

Demographic | AP Votecast | National Election Pool | Average
:---------- | :---------: | :--------------------: | ------:
No degree   | -4%         | -2%                    | -3%
Degree      | 16%         | 12%                    | 14%
Less than $50,000 | 8%    | 11%                    | 10%
$50,000 to $99,999 | -2%  | 15%                    | 7%
More than $100,000 | 4%   | -12%                   | -4%

I think these changes &mdash; greater polarisation along education lines and contiued polarisation along income lines &mdash; are driven by the nature of value divides in American politics. To show this, I used several questions that the American National Election Study has asked for the last few decades to construct indices of economic left-right values and social liberal-conservative values that are consistent over time. Using an approach similar to the one above, I estimated the effect of each index on vote choice in every presidential election since 1992. I derived these indices by running a principal component analysis on questions about government healthcare, guaranteed jobs and income, aid to black people and other minorities, the legality of abortion, the authority of the Bible, views on affirmative action, support for laws banning job discrimination against LGBT workers, and opinions on immigration.

<img src="{{site.baseurl}}/assets/img/econsocvote.png" alt="Presidential vote share by economic and social values" style="zoom:50%;" />

As you can see, social values have had an increasingly strong effect on vote choice since the 2008 election. Of all the elections for which I could construct an index, social values had the strongest effect in the 2016 presidential election. For anyone who experienced the 2016 election campaign, this is hardly surprising. Not only did Trump's statements about immigrants, minorities, and women make social values a key part of the election, the Clinton campaign chose to lean into this by emphasising Trump's offensive statements in campaign advertising rather than economic issues. Contrast [this](https://pcl.stanford.edu/campaigns/2016/?adv=What+He+Believes) Clinton advertisement from 2016 with [this](https://pcl.stanford.edu/campaigns/2012/?adv=Revealed+%28OH%29+-+Barack+Obama+-+Jun+26) Obama advertisment from 2012. In 2012, the Obama campaign focused heavily on manufacturing jobs and on Mitt Romney's record on outsourcing when he was part of Bain Capital. Despite Trump's litany of worker rights violations, penchant for outsourcing (of his own Make America Great Again hats!) manufacturing to China, and history of hiring undocumented immigrants, he was able to take ownership of the deindustrialisation issue. Clinton's past statements on the inevitability of outsourcing and deindustrialisation, even if they were true (something that I must remind you Barack Obama would have vehemently disagreed with in 2008 and 2012), didn't help this. This helped to make the 2016 election more about social values and less about economic values than past elections.

How does this tie into income and education voting patterns? For this I looked at how positions on the economic and social values scales varied by income and education level.

<img src="{{site.baseurl}}/assets/img/lrecon.png" alt="Left-right values by income and education" style="zoom:50%;" />

For left-right values, higher income has the expected effect of making someone more right-wing. This is why we should expect that elections polarised around economic issues, like the 2008 and 2012 elections, would make income more predictive of vote choice. Interestingly, education seems to mediate the impact of income on left-right ideology; voters with higher education attainment tend to be more supportive of redistribution. This is potentially because education makes people more universalistic and altruistic, so individuals with degrees will be more likely to disregard their own economic interests when deciding whether to support redistribution. There is also a documented link between attitudes towards redistribution and racism in the United States[^9], which might indicate that education impacts left-right values because it reduces racial resentment.

<img src="{{site.baseurl}}/assets/img/libconsocial.png" alt="Liberal-conservative values by income and education" style="zoom:50%;" />

Moving on to social values, both higher income and higher education tend to make people hold more liberal views (though education has a much stronger impact than income does). This indicates that when the electorate is polarised on social values, lower income voters will become more likely to support the right and higher income voters more likey to support the left. This is exactly what we see in the 2016 election from my analysis of ANES data; without controlling for education, the top 5% was actually more likely to vote for Clinton than the bottom 16% was. 

The question for the future is whether American politics will continue to be polarised on both economic and social lines. The last two elections (2018 midterms and 2020 presidential election) have shown that when economic issues are back on the agenda, the working class moves further into the Democratic column. But the events of the last few years, from the Charlottesville rally in 2017 to the tragic death of George Floyd earlier this year and many more, show that racism is alive and well in the US, so we can expect the newly strong education cleavage to remain. Biden's losses among minority voters in the last election raise questions about why the race cleavage might be slipping even as racism is near the top of the political agenda, but that's a question I do not have an answer to. What I hope to have shown in this post is that the American electorate is still divided on class lines and that neither Donald Trump nor any Republican has managed to sever the link between the working class and the Democratic party. As much as some Republicans, like Florida Senators Rick Scott[^10] and Marco Rubio[^11], might talk about a "multiethnic, working class coalition" of Republican voters, there is very little evidence to indicate that it exists. And unless Republicans stop unashamedly siding with the interests of capital over labour through their policies on taxes, healthcare, spending on social programmes, and labour market regulations, I don't foresee this image becoming a reality.

[^1]: Cohn, N. (2016). There Are More White Voters Than People Think. That’s Good News for Trump. *New York Times*, *The Upshot* <https://www.nytimes.com/2016/06/10/upshot/there-are-more-white-voters-than-people-think-thats-good-news-for-trump.html>

[^2]: Reny, T., Collingwood, L., & Valenzuela, A. (2019). Vote Switching in the 2016 Election: How Racial and Immigration Attitudes, Not Economics, Explain Shifts in White Voting, *Public Opinion Quarterly*, 83(1), pp. 91–113, <https://doi.org/10.1093/poq/nfz011>

[^3]: Carnes, N., & Lupu, N. (2020). The White Working Class and the 2016 Election. *Perspectives on Politics*, pp. 1-18. <https://doi.org/10.1017/S1537592720001267>

[^4]: Kennedy, C. et al. (2018). An Evaluation of the 2016 Election Polls in the United States. *Public Opinion Quarterly*, 82(1), pp. 1–33. <https://doi.org/10.1093/poq/nfx047>

[^5]: Kim, C., Tamborini, C., & Sakamoto, A. (2018). The Sources of Life Chances: Does Education, ClassCategory, Occupation, or Short-Term EarningsPredict 20-Year Long-Term Earnings? *Sociological Science*, 5(9), pp. 206-233. <https://doi.org/10.15195/v5.a9>

[^6]: Zhang, C., & Burn-Murdoch, J. (2020). By numbers: how the US voted in 2020 *The Financial Times* <https://www.ft.com/content/69f3206f-37a7-4561-bebf-5929e7df850d>

[^7]: Brooks, C., & Manza, J. (1997). Social Cleavages and Political Alignments: US Presidential Election, 1960 to 1992. *American Sociological Review*, 62(6), pp. 937-946. <https://doi.org/10.2307/2657348>

[^8]: Ghitza, Y., & Gelman, A. (2013). Deep Interactions with MRP: Election Turnout and Voting Patterns Among Small Electoral Subgroups. *American Journal of Political Science*, 57(3), pp. 762-776

[^9]: Alesina, A., & Glaeser, E. (2004). 'Race and Redistribution' in Alesina, A., & Glaeser, E. (eds.) *Fighting Poverty in the US and Europe: A World of Difference*. Oxford University Press, pp. 133-182.

[^10]: <https://floridapolitics.com/archives/386998-rick-scott-says-gop-can-win-if-it-talks-to-latinos-working-class-whites>

[^11]: <https://thehill.com/homenews/news/525585-rubio-gop-must-rebrand-as-party-of-multiethnic-multiracial-working-class-voters>