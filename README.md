# Fan-Predictor


## Step 0 - Machine Learning Project starting point 
This is a Machine Learning project I started because of personal interest. The idea of this project is basically to see if it is possible to predict the number of visitors for amateur football games (=match) in Austria. I was thinking of the amount of people that are watching the games of the club I am currently playing at. It was clear to me that the number of fans watching was dependent on the current weather and also the away team we were about to face. In all situations the number of fans would never exceed the number of available seats, so it is never the case that we would have to turn the opportunity down for someone to watch the game. The consequence is that the only thing you can rely on to estimate the number of watching fans is a gut feeling and past experience. Why probably leads to poor planning of the needed food, drinks and stuff. 

Then the idea came to my mind: Why not start building a model that can predict the number of fans that will come and watch the game? At that time I didn't even have an idea if this could work. I didn't even know if there was data available I could use. To be honest, we are talking about amateur clubs, so maybe no one even cares about to number of fans. 

I quickly made a list of plausible data I would need and where I could get them: 
* weather on matchday -> there is probably some weather API I can use
* standings on matchday -> can probably scrape that
* geographical distance between the two teams -> some geo API I can use
* league -> can probably scrape that
* date of matchday -> can probably scrape that
* start of the match -> can probably scrape that
* fans of past matches = LABELS -> is this data even somewhere available?

Luckily, after a quick Google search I found out that the needed labels and the other data are available on a website I can scrape (more on that later).

I have no idea if this could really work or if there are features that I need to add to make it work, but to start I think this is enough to start a try. At least this is also the data one would look at to get an idea of how many fans would come. Let's see if we can improve on these inaccurate predictions based on gut feelings. 

## Step 1: Define the objectives
* Outputs/Labels: The problem we are facing is a regression problem - we are trying to predict a continous number
* Failure/Mistakes: In general we could consider both, predicting more fans or less fans, as equally bad. Since the main idea of this project is to reducde food waste by better prediction of fans we take the side of too high demand/fan prediction is more bad than lower estimates. 
* Business Performance Metric (BPM): We choose the __Mean Absolut Error (MAE)__ as the BPM. It captures the essence of what we are looking for and not that sensitive to "outliers" (e.g. games with more fans, since it is a so called [city derby](https://dictionary.cambridge.org/dictionary/english/local-derby)), which may be harder for the model to learn. 
* Loss: Since there may be games with higher fans, we still want our model to at least not completly fail at those predictions. Especially these predictions are of special interest to deliver a good forecast, because we could then see the model has learned the patterns. So MAE also as Loss function is not quite what we want. We will go for the __[Huber Loss](https://en.wikipedia.org/wiki/Huber_loss#Pseudo-Huber_loss_function)__. It provides a middle between MAE and the more outlier focused Mean Squared Error (MSE).


