+++
title = "gg Bar plot graphing"
weight = 20
draft = false
+++

Download and catalogue the required packages

```[r]
library(Lahman)
library(sqldf)
library(ggplot2)
```[r]

Extract the information needed from Lahman, homeruns from teams in the year 1980 ordered by homeruns.

```[r]
query<-"SELECT name,HR
FROM Teams
WHERE yearID=1980
ORDER BY HR"

result<-sqldf(query)

result$name<-factor(result$name,levels=result$name)
```[r]

Now we visualized the data in the bar plot

```[r]
ggplot()+
  geom_bar(data=result,aes(x=name,y=HR),stat='identity',color='blue',fill='white')+
  coord_flip()+
  ylab("homeruns")+
  xlab("team")+
  ggtitle("1980 Team Homeruns Distribution")
  ```[r]