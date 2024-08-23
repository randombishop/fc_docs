# Farcaster Data Analytics Project

Welcome to this Data Science Art experiment!

I built it to explore the Farcaster protocol and run ML experiments in this rich playground.

Hope you'll find it useful or educational. Feel free to reach out if you have any questions or feedback.

## Overview

What I buily so far:
![Farcaster Data Analytics Schema](schema.png)
* A Farcaster Hub with shuttle to replicate data to a Postgres DB.
* A couple of ML models to classify the casts and calculate embeddings and features such as sentiment, informational, funny. Those are built as python workers.
* A Big Query dataset with clean and rich data easy to query. 
* And finally, 2 ways to query and view the data: through a web app, or by asking a bot to run a function.


## Airflow ETL
If you want to know exactly how the data is preprocessed, you can check out the source code of my ETL here:
[fc_airflow repository](https://github.com/randombishop/fc_airflow)


## Big Query Dataset
The Big Query dataset provides a data perspective that is different from what you can find in Dune dashboards. 

For example. rather than having all the links events, it has a single table that represents the social graph with one row per follower/followed.

It also has a table with one aggregated row per user_origin/user_target with the total count of likes, replies and recasts.

Finally, in the casts table, you will find embeddings, usefull for ML tasks, category and topic classification, plus interesting features coming from the Gambit model and Likemeter. (more on these on the sections below.)

The dataset description is available [here](dataset.md)

It can be queried directly from the [web app](https://app.datascience.art/#/bot) or by tagging @dsart on Farcaster.

## Gambit model
The Gambit model is a NN that uses a 512 embedding of the cast as input, and classifies it into categories, topics, reduces the embedding to 32 dimensions, and also adds the following interesting features:
* Is it clear?
* Does it have a clear target audience?
* Is it informative?
* Is it easy to understand for the general layman public?
* Is it verifiable online?
* Is it personal?
* Is it funny?
* Is it a reference to a well known meme?
* Does it elicit an emotional response?
* Does it convey happiness?
* Does it trigger curiosity?
* Is it aggressive?
* Does it have an element of surprise?
* Does it ask an interesting question?
* Does it come with an explicit call to action?


## Likemeter
The likemeter uses the features generated by the Gambit model to predict if a cast will be liked/recasted/replied-to.


## The Bot
The @dsart bot is a cool way to run the functions defined [here](https://github.com/randombishop/fc_bots/blob/main/bots/functions.md).

You can send requests like these by simply tagging @dsart and will get a reply:
* Who are @dwr.eth's favorite users?
* Who is most active in /data channel
* Give me a bitcoin summary
* Show me the funniest cast in tabletop channel

I am excited to add more functions too, I am thinking some fun stuff like:
* What does @vitalik.eth post about?
* What does @v like, reply or recast? 
* What are my favorite topics? 
* Psychoanalyze user @ted
* Roast me!

I open sourced the [repo](https://github.com/randombishop/fc_bots) and hope the community will propose and contribute more functions too!


## The Web App
[https://www.datascience.art/](https://www.datascience.art/)
