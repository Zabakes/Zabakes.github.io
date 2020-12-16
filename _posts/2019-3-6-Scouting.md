---
layout: post
categories: posts
title: SCOUTING DATA DASHBOARD
tags: [CODE, Python, FRC 333]
date-string: March 6, 2019
featured-image: \images\ScoutingAppMain.png
---
<left>
I built this scouting app with Plotly, Numpy, Pandas, and a couple other libraries, for, pulling data from google sheets and the blue alliance API. I would check on this dashboard in the pits to better understand what the teams on my alliance could do. Having real time data about a team's performance made strategizing so much easier. We could then use this dashboard during our scouting meetings to see a team's performance and pick specific matches to watch after we narrowed down our selections.
</left>

<br>
<br>

<center>
<img src=" \images\ScoutingAppMain.png" alt="Example">
<H1>Main Screen</H1>
<p>
This screen was designed to view an individual team's performance. You would first select a team from the dropdown on the top of the screen. Then their data would populate all the graphs. The bar chart on the top has its own dropdown where you can select from a list of all the numeric categories. This means can give you a good idea of how a team performs on average. The second graph shows you a team's score by match in blue and, their alliance's score in orange. The team's individual score is calculated based on scouting data our team collects in google forms. This data is then pulled from a google sheet automatically by the python code. The code then pulls the alliance's score from the blue alliance. We do this because the data from the blue alliance is more reliable than the data our scouts collect. On this same graph there's a green dot on the match(es) where the team plays the most defense. This lets us go back and watch that match to see how a team defends/drives. Finally, there's a chart showing what level(s) a team has gotten to in the endgame period, as well as a chart showing how much a team plays defense.
</p>

<br>
<br>

<img src=" \images\ScoutingAppRadar.png" alt="Example">
<H1>Radar Chart</H1>
<p>
While the other page lets you view a team's performance on its own, this screen lets you compare two teams. You can select teams from the upper dropdown, then select categories to compare in the lower dropdown. Then the python app builds a radar chart using Plotly based on the selected teams and categories. This is useful when trying to compare two or more teams for alliance selection.
</p>
</center>