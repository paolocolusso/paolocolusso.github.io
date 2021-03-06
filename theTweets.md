---
layout: page
title: The Words
subtitle: Looking into the 140 characters.
---

If, as we claim, Russian trolls aim at spurring political instability in Europe, it is natural that they should focus on disruptive events showing the weaknesses of our society. Also, they would probably touch upon themes that are likely to cause controversy and that are key in the political agenda of populist parties: they would naturally encourage political debate, creating divisiveness in the country.

What we see is in the following analysis is indeed that they are more active during periods coinciding with peaks of terrorism in Europe, migratory crisis and political events: in other words, trolls never cease to provoke controversy by referring to delicate issues (migration), both at national and international level. 


### Content analysis
We finally delve into the content of the tweets themselves, starting by a general overview. Which words are occurring the most? 

![](../img/word1.png){: .align-center}

Italian readers will notice that most of the words are names of **newspapers** and press agencies, with a peculiarity: it is hard to spot the the presence of radical papers. *la Repubblica* is the best-selling Italian paper, followed by *Corriere della Sera* and *La Stampa*, while *ANSA* is the main press agency. Although *la Repubblica* is rather centre-left wing, all of these are generally perceived to be as **moderate** and **reliable sources** by the majority of the population: this is probably also the impression trolls want to give.

If we now exclude papers and press agencies from the cloud, a clearer picture emerges: politics is clearly on top when it comes to favourite topics for trolls. 

![](../img/word2.png){: .align-center}

If we look at **national politics**, all the themes which have determined the results of the most recent elections are there: **migrants**, **Europe**, **security**. The name of the main parties is also present, together with some leaders' name. Although *Renzi* and *Democartic Party*, *PD*, are of larger size than their political opponents, other parties are more represented in terms of political priorities: *migrants* and *security* are the main target of the *League*, for example. Taking a further look at the output of the word cloud, one will notice that words associated to the *PD* crisis feature highly (corruption scandals, internal fight for the leadership of the party...).

Shifting to **international politics**, Trump is the big name. More generally, the words mainly refer to the weaknesses of the European Union: **terror attacks**, **Brexit**, the **common currency**... The lexicon seem to be dominated by negative words, which conveys the idea of the current situation in Europe being doomed. But there is more to it. Except for Germany and France, the countries mentioned have one common feature: they are ruled by authoritarian leaders: **Turkey** (Erdogan), **Syria** (Assad), **Russia** (Putin). A similar idea holds for **Trump**, which is typically perceived as strong and tough, especially in terms of migration. Also, notice that Syria is the one of the main interests of the Russian foreign politics.

Laslty, words as **fear**, **terror**, **risk**, **terrorism**, **massacre**, **attack** clearly want to stress a situation of instability.

It is hardly surprising that Russia would try to provide a negative picture of our institutions: lack of faith in traditional parties and institutions has already lead towards increased success of populist parties all across Europe, making it weaker. Stressing social problems and political crisis or terrorism usually leads countries to look for easier answers, like nationalism: this creates sympathy towards more authoritative figures, like Putin and Trump, who present themselves as strong in defending their country's interests.

### Topic detection
We can now turn to machine learning to spot groups of tweets by means of clustering, hoping to identify main topics in the trolls' discussions.

Among the most represented terms in the clusters we obtain are:

+ **Cluster 1**: italy, roma, renzi, pd, napoli, macron, europa, milano, alitalia, blog, ue, migrants, ...

+ **Cluster 2**: rt, adnkronos, repubblica, **elena07617349**, corriere, leggoit, agenzia_ansa, lastampa, ilpost, ...

+ **Cluster 3**: trump, usa, corea, nord, siria, repubblica, **wall**, pyongyang, threat, test, russia, war, china, attack, missiles, nuclear, obama

Machine learning groups together national and European issues on one side and big international challenges on the other. The Syrian and Korean issues seem to have a key role in defining the cluster, but American politics comes in with Obama, Trump and the wall (in all likelihood the one with Mexico). The remaining cluster probably points to general news reports, related to local facts or episodes.

A visual representation, obtained by PCA, shows the separation is indeed quite effective.


![](../img/cluster.png){: .align-center}


### Words often appearing together
We now use data mining, and specifically association rules, to confirm some intuitions.

In tweets related to Italian politics there is a big difference from the traditional Democratic Party, who is associated to its internal fights and scandals, and the populist Five-Star Movement, who often goes together with references to the official blog of the party.


| Antecedent   | Consequent     | Confidence    |
| :---         |     :---:      |          ---: |
| elections    | pd             | 0.888889      |
| consip       | renzi          | 0.297297      |
| grillo       | m5s            | 0.272727      |
| grillo       | blog           | 0.265152      |


International politics is again dominated by the big leaders: interestingly, Trump is associated with Putin. Notice also that there is a frequent association between Macron and Lepen, whose political story somewhat mirrors that of Renzi and Salvini.


| Antecedent   | Consequent     | Confidence    |
| :---         |     :---:      |          ---: |
| lepen        | macron         | 0.790698      |
| putin        | trump          | 0.290909      |
| missiles     | syria          | 0.586207      |


As we were noticing, trolls never cease to stress instability: Stockholm, for instance, gets matched with the truck which caused a massacre in the 2017 terror attack, while London follows Westminster, where an attack took place in 2017.

| Antecedent   | Consequent     | Confidence    |
| :---         |     :---:      |          ---: |
| westminster  | london         | 0.763636      |
| stockholm    | truck          | 0.392857      |
| at least     | deaths         | 0.394958      |
| deaths       | injured        | 0.201258      |



### Speaking about politics

As we saw, the debate proposed by trolls mainly revolves around politics: who is the most discussed politician in troll tweets?

In counting the number of tweets where politicians and parties are mentioned, we separate the analysis for mentions by prolific trolls (the ones who publish more tweets) and the whole trolls' population, to see if IRA specifically concentrate the activity of frequent users to highlight particular ideas.


![](../img/poli_ments.png){: .align-center}

We repeat the same question for political parties.


![](../img/parties_ments.png){: .align-center}

Although it might seem that the Democrats are being favoured, it must be noticed that:
+ during the period considered the government coalition was lead by *PD*, so that it is natural that they should be more present in the discussion, 
+ a mention *per se* is not necessarily positive, as the tweet might be critical, something we will come back to...

Lastly, the prolific authors do not seem to have a prominent role, as the fraction of their tweets is consistent across the parties and with the whole dataset.

### Sentiment Analysis

What is the general sentiment of these tweets if we consider politicians separately?

|              | Negative       | Neutral       | Positive      | Compound      |
| :---         |     :---:      |     :---:     |     :---:     |     :---:     |
| Renzi        | 0.12           | 0.75          | 0.13          | 0.06          |
| Salvini      | 0.12           | 0.75          | 0.13          | 0.09          |
| Grillo       | 0.13           | 0.75          | 0.12          | 0.04          |


In terms of political parties the result is instead the following.


|              | Negative       | Neutral       | Positive      | Compound      |
| :---         |     :---:      |     :---:     |     :---:     |     :---:     |
| PD           | 0.12           | 0.75          | 0.13          | 0.1           |
| Lega         | 0.12           | 0.75          | 0.13          | 0.1           |
| M5S          | 0.13           | 0.75          | 0.11          | -0.02         |


The tables and the following plot show that there is no striking difference between the sentiment for tweets related to different parties, although the compound sentiment for *M5S* is slightly more negative. This might be explained by the aggressive tones used by members of this party  (think for instance to the *V day*, which stands for *fuck off* day in Italian, a public demonstration held by Beppe Grillo in 2007 against corrupted politicians).


![](../img/sents.png){: .align-center}

The results seem to show that trolls do not have a clear favourite, but try to spread their critical point of view among the different parties. The remainder of this section indeed presents some of the tweets to see this fact in practice.

### The tweets!


Starting from the **Five-Star Movement**, we immediately see that there are mixed feelings: tweets range from paying homage to the cofounder of M5S to the criticism of a spiteful attitude. A link between the crisis of PD and the success of the M5S is also proposed.  


![](../img/t1.png){: .align-center}
![](../img/t2.png){: .align-center}
![](../img/t3.png){: .align-center}

Talking about **PD**, however, the situation changes: it becomes harder to find tweets in support of the party, as mentions to it are only due to its crisis, to the internal fights, or are plain critics. Some users talk about a poisonous environment, some claim the party celebrates fascism and some others are critical towards the choices made in the Budget.

![](../img/t4.png){: .align-center}
![](../img/t5.png){: .align-center}
![](../img/t6.png){: .align-center}
![](../img/t7.png){: .align-center}
![](../img/t8.png){: .align-center}
![](../img/t9.png){: .align-center}

Like for M5S, tweets on the **League** are also ambiguous, but unlike what happens for PD, some users mention typical themes of the League, such as the EU and the mishandling of migrants.

![](../img/t10.png){: .align-center}
![](../img/t12.png){: .align-center}
![](../img/t13.png){: .align-center}

The last tweet, however, despite sharing a key message of the party, hides some irony for the fact that Salvini spent one day taking selfies and enjoying Sicilian's delicatessens. 

## Some conclusions

Although trolls sometimes talk about football and music (take a careful look at the wordcloud and see if you can spot words related to this!), their main interests lie elsewhere. The general tendency seems to be to engage as wide a public as possible and to foster strong political opinions, in all directions. As any Italian will know, there is nothing which causes as much controversy as do immigrants or Europe... so trolls are somehow playing it safe when often referring to migration. In terms of politicians, while the content analysis seems to show Democrats are penalised, the sentiments point to a homogeneous treatment of all the political actors (with the slight exception of the compound sentiment for the Five-Star Movement).

