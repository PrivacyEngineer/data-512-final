# Analysis of Tweeter Activity for the 115th Congress of the United States of America.

## Context

Much has been said and written about the increasing widening of the partisan divide that has characterized politics in the United States over the past three decades. Republicans and democrats may always have had ideological differences, but starting sometime in the mid 1990s, reconciling such differences in order to present a united front against challenges the country faces, has gradually become more and more difficult. To an external observer, it seems like having one party drift in a certain direction with respect to a particular issue is more than enough to have the other party react in the oposite direction, regardless of what the issue is, and regardless of whether either position is even remotely reasonable. This partisan divide has slowly, and very unfortunately, permeated to the general population, as is painfully obvious to anyone who has spent any time on Facebook, Twitter, Reddit forums and other social media and news aggregation websites.
In spite of these facts, public discourse by politicians largely kept an acceptable level of decorum throughout the Clinton, Bush and Obama administrations. Starting with the presidential campaign of 2016, however, the now president of the United States of America has often abandoned decorum and restraint in his public appearances and communications, particularly those that take place over Twiter.
There is also a significant amount of anecdotal evidence that seems to suggest that the racism, xenophobia, aggressive partisanship, inaccuracies, contradictions, and general unpleasantness of the president's communication style have been interpreted by some as providing implicit approval for the unrestrained expression of similar feelings and beliefs and, on occasion, for acting upon them. If this is correct and members of the U.S. 115th Congress, many of them elected or reelected in 2016, are following suit, then this effect will be amplified.

## Research questions

For this project we will look at whether the 115th Congress of the United States of America, 100 senators and 435 representatives, have been influenced by, and contributed to this overall toxicity trend, as evidenced by the messages they tweeted between January 27th 2017 and July 20th 2018.
Our plan is to use a number of machine learning models that can be accessed through Google's Perspective API, to score each of a collection of tweets written by members of Congress over the aforementioned period. Besides providing a probability score of the toxicity, or lack thereof, of a particular tweet, these models also provide scores for specific types of toxicity, such as attacks on identity and individuals, threats, use of sexually explicit references, inflammatory and incoherent messages.
The specific questions we plan to ask are:

- Did the level of toxicity in Tweeter communications from members of Congress increase over this period?
- If it did, can we identify increases of specific types of toxicity, like racism and xenophobia?
- Has the level of toxicity been greater in tweets from either party?
- Who were the most toxic congress members over this period of time?
- What other inferences can we make from the results of our analysis?

## Process and sources of data

These are the data sources and APIs we will access in order to obtain the data needed for our analysis:

- We begin with a dataset containing the tweet identification numbers for over 1.8 million messages tweeted from the official accounts of members of Congress, available from Littman, Justin, 2017, "115th U.S. Congress Tweet Ids", https://doi.org/10.7910/DVN/UIVHQR. This dataset is made available under the Creative Commons CC0 - Public Domain Dedication license: https://creativecommons.org/publicdomain/zero/1.0/. That is: "The person who associated a work with this deed has dedicated the work to the public domain by waiving all of his or her rights to the work worldwide under copyright law, including all related and neighboring rights, to the extent allowed by law."
- Twitter's developer policy, Section F.2, found at https://developer.twitter.com/en/developer-terms/policy, indicates that "If you provide Twitter Content to third parties, including downloadable datasets of Twitter Content or an API that returns Twitter Content, you will distribut or allow download of Tweet IDs, Direct Message IDs ad/or User IDs," the above tweet IDs need to be "rehydrated." That is, we use a tool called "Hydrator" to feed the tweet IDs to the Twitter API and recover the tweets themselves directly from the source. The Hydrator tool is provided by DocNow (https://www.docnow.io), who makes it available under the MIT license at https://github.com/DocNow/hydrator. Twitter provides access to its API under its own terms of service: https://twitter.com/en/tos.
- Once we have recovered the tweets themselves, we will use Google's Perspective API, https://github.com/conversationai/perspectiveapi/blob/master/api_reference.md#models, to have each tweet scored for toxicity, as well as for sub-classifications of toxicity, such as attacks on identity, personal attacks, sexually explicit references and others. Google provides access to its APIs under their own terms of service:  https://help.github.com/articles/github-terms-of-service/.

Given the context in which these tweets are being sent, our expectation is that we will find an significant increase in overall toxicity in this period. In particular, we expect to find increase of positive classifications in models related to identity, which would correlate with race and xenophobia, attacks on authors of tweets, inflammatory rhetoric and profanity.

## Unknowns and dependencies of our project

At the time of the writing of this proposal we have acquired the dataset of tweet identification numbers and rehydrated the tweets. We have also tested the Perspective API, and seen that it works with a small tweet test set. An analysis of the licenses and terms of service that were referenced in the previous section has indicated that there are no legal roadblocks to execution of this project. Nevertheless, we may still not be able to complete this project successfully if:

- Request rate limits in the use of the Perspective API make it impossible for us to analyze all tweets in the dataset.
- The toxicity scores obtained from the use of the Perspective API deviate significantly from the actual toxicity of the content. That is, if the number of either false positives or false negatives, or both, is too high.
- There is also the possibility that our findings will turn out to be negative. That is, if Congress member's Twitter communications have maintained decorum and civility over the analyzed period of time, or if the number of toxic tweets of specific sub-categories turns out to be too small.
- It is important to point out that the previously cited Twitter developer policy also states, Section F.2.ii.a, that "You may not distribute Tweet IDs for the purposes of (a) enabling any entity to store and analyze Tweets for a period exceeding 30 days unless you are doing so on behalf of an academic institution and for the sole purpose of non-commercial research ..." Given that this project is taking place in the context of a formal course at the University of Washington, we believe we meet the bar to include the tweet ID lists along with our final project submission. Having said that, we have to verify this conclusion and may, in the end, not be able to include these lists in our publication.

## Human Centered Data Science

This project is most directly related to the societal implications of data science, as it shows how data science can be used to analyze various aspects of human communication and what is going on in specific areas of human interaction. It may also turn out to be a good case study on the consequences of biased data, if we consider written human communication as data that feeds into our own prejudices and biases when reacting to events and other people's claims and vitriol.