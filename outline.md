# NCAUG 2017 Presentation

## Abstract

The City of Raleigh Parks, Recreation & Cultural Resources department tasked its GIS
section to assist with a goal to improve access to existing and future parks. The project
analyzes about 150 Raleigh parks and prioritizes access improvement opportunities
with the use of ArcGIS Network Analyst and custom tools built with Model Builder and
ArcPy. By examining citizen access, this analysis suggests opportunities to increase
the park system's level of service through expansion of access to current parks rather
than just land acquisition or new park development.

## Outline

### Introduction

My name is Ryan Cooper and I'm a Senior Systems Analyst/Programmer with the City of Raleigh Parks, Recreation and Cultural Resources Department. I'm here to speak to you all today about some of the ongoing work our department is doing to try and improve park access to the citizens of Raleigh. Specifically, I'll be talking about how we are using GIS to gain a clearer understanding of the over all level of service of our park system, where there are localized opportunities to improve access, and what those form that improvement might take.

If you were at the state GIS conference in February, you might already be a little familiar with some of what I'm presenting. What I'll be talking about builds upon the Experience Based Park Access Model that emerged as the winner of the Herb Stout Award at that conference. Although our department is proud of that award I bring it up so that I may point out that much of what I'm presenting today is a result of a lot of teamwork and vision from people across our department, much of work predates my involvement with this work. I'd be remiss if I didn't acknowledge Rob Siwiec who is responsible for the lion's share of the code and logic behind our analysis. He has moved on to Wake County Public Schools, but his fingerprints are all over this project and he deserves a lot of credit for the work I'm presenting. Many thanks to Rob.

### What are we going to talk about?

So let's talk about the shape of the rest of this presentation.

1. Brief overview of the motivation for the EBPA
2. Explanation for how the EBPA works
3. Brief overview of the Neighborhood and Community Connections Program
4. Explanation for how the NCC scripts work
5. Challenges and opportunities

### What is the Experience-Based Park Access Model?

The Experience-Based Park Access Model is new way of essentially determining the level of service our system provides to our citizens at the Census Block and Block Group level. It focuses on parks that provide a core experience (walking/riding a bike, open play, playground, places to socialize) and how much of the population within 1.29 miles have access to those types of parks. All in all, it helps us see where our citizens are well served by the parks system and where there is room for improvement.

This model also helps us understand where access improvements might be possible for improving level of service. I'll get to this in a moment, but essentially, it helps us see a range of options for improving level of service. Maybe we do need to acquire land, go through the master planning process, and construct a new park. But maybe there are some cases where improving sidewalk connectivity or adding a new entrance will open up a park to a significantly greater number of people in the area.

Finally, we can use the model to think about where to add new amenities or where to acquire new land.

### Why an experience-based model?

Raleigh is a city that loves its parks, so much so that it is sometimes described as "a city within a park". Massive population growth over the past 30+ years has meant the parks system has had to grow as well. Helping to inform where our department acquires and develops property has been a level of service measure from 1917 that states "The area of parks and other public grounds within the city apparently presents the most satisfactory basis for computing the relation of population to recreational areas." In short, level of service is the population per acre of park land.

This measure has some shortcomings. First, it looks at the city as a whole and thus ignores the possibility that park amenities might be unevenly distributed. Second, it is a measure that is good for comparing level of service against other cities, but not for understanding level of service throughout our city. Our overall level of service compared to Charlotte, Wilmington, or Greensboro doesn't mean anything to the citizen whose taxes pay for our parks but is better served by Cary or Wake Forest.

Now, we were able to ameliorate some of this by looking at population within a given distance of each park. But this also was insufficient because it involved drawing a uniform buffer around a park and calculating the population within the buffer. While this was better than just taking the city as a whole, the use of a uniform buffer only accounted for Euclidean, straight-line distance to the park; not the actual distance people have to travel along the road to the park.

Furthermore, this measure of level of service looked at park properties as a homogenous entity. It doesn't really fit well with the way park land is acquired and developed. Undeveloped land presents a different experience than one with a playground, basketball court, etc. Certainly there is utility in knowing what assets we have an maintain. But that is a consideration of how our department interacts with the parks, not our citizens. If we are trying to get a hold of our level of service for our citizens, we need to account for where we are really providing service to our citizens. This previous model didn't really have the nuance we wanted.

### Metrics

So we came up with some values and metrics to use to get a better grasp of how we're serving our population.

### PRCR approach

This sort of course grained model wasn't really cutting it. So a different way of approaching level of service was developed. Having GIS technology and a good store of data about our parks meant that we could carry out a more nuanced analysis of our system.

In particular, we wanted a model that was more than a snapshot of assets, and rather a consideration of our citizens' experience of our parks system. Certainly there is utility in knowing what land we have, but a median that is technically ours needs to be considered differently from a park with a playground and basketball hoops. So as we've developed this model, we've taken special care to focus on those properties that provide or have the potential to provide a core experience (open play, walking/riding a bike, sitting, playground).

We also wanted to consider park accessibility. Not all parks are equally accessible by all residents. So we broke down the city into Census Blocks and consider how many people live within 1.29 miles of a given park - I'll talk about where that number came from momentarily.



the Experience Based Park Access Model was developed to help address some key issues:

- Need to generate performance measures related to level of service
- Help target improvements to existing parks and greenways
- Help determine where to add new parks or develop existing park land
- Identify areas for land acquisition

### Goals

#### Work out the numbers

Maps, charts, and lists carry with them visual authority. However the decisions that go into the data generating the these sorts of data visualizations are products of the people generating the data. While striving for an objective measure of access is our goal, we have made decisions along the way about what we measure and how, what we don't measure, and how to combine all these measures together to get to a seemingly definitive single value for each Census Block that represents park accessibility. A lot of work has gone into what factors we measure so that a variety of concerns about access are accounted for in the model. However, we have a had some difficulty figuring out how to combine the values for each factor into a single accessibility score. Right now we are using ranking each block for each factor, adding those together, an re-ranking based on the sum. While this does give us a common value to compare census blocks across factors we can't tell by how much each block varies from the other. In other words, we can figure out what the top three census blocks for circuitry are, but once we rank them, we lose any sense of how those scores are dispersed. We only know that 1st is better than 2nd is better than 3rd. One of our challenges is to normalize the score for our factors so that when they are combined, we can measure not only which block has the best access, but also by how much.  

#### Make the EBPA accessible

It is somewhat ironic that our accessibility model is largely inaccessible. There are currently exactly 2 people who can run it. As it is, this doesn't bode well for the sustainability of this model. It is also fairly tightly connected to City of Raleigh data. While the model could be adapted for other places and for different domains, it would take quite a bit of work. So there are some things we are currently doing and that I hope to do to make the EBPA model more accessible.

##### Documentation

Some documentation exists for the model, but it suffers from being a bit sparse on some details and also spread across several Word documents. In order to make this accessible to more than just me and Rob, there needs to be some documentation that is detailed and searchable. Part of my work in trying to learn how to use the EBPA model has been filling in the gaps in the existing documentation and consolidating them into a single, searchable source. To help facilitate this I've been using a Python documentation site generator called mkdocs. MKDOCS is great because you can write up the docs in a text file. With some minimal Markdown formatting, a page of docs is rendered in an aesthetically pleasing way and is made searchable. Now if I need a reminder of how to build the road network dataset, I can just search that and navigate to the appropriate page.

##### From Esri to More-Than-Esri

Currently the model is very wedded to Esri tools. Beyond ArcPy, the model depends on Network Analyst, Model Builder, Esri Demographic Enrichment data, and ArcGIS Pro. These are great tools that have helped us to develop this model relatively quickly. However the dependence solely on Esri tools means we are limiting who has the ability to use this model. I believe this model has the potential to be useful for more than just municipal government departments. Community advocacy organizations, environmental groups, non-profits and more could be able to run analysis based on the logic of this model. However, many of these groups do not have the resources to afford Esri's offerings. Even some Esri shops may not have the necessary Advanced license, Network Analyst license, or service credit availability to run the model. As such, I am interested in disentangling the dependence on Esri tools so that we can make this accessible to a wider range of organizations. The open source geospatial landscape includes a lot of amazing tools like shapely, ogr, gdal, PostGIS, pgRouting, Pandas, GeoPandas, and many more tools that could be use to replace some of that dependence on Esri tools. And while I think it would be great to make this model built fully on open source software, even getting it to a point where it could be run with a Basic ArcGIS license would be a real win for making the model accessible to more organizations.

##### Open Source

We're a long way from open sourcing this model, but I think it's a goal worth working towards. This code needs to be available to be used by others. First, there is an argument to made that algorithms that are used for making decisions on the public's behalf should be accessible by the public. We already recognize that there are community benefits in making data readily available to the public. It doesn't seem unreasonable that the public should also be able to access the code that is being used to shape their community. Currently this is [something that has been proposed](https://www.nytimes.com/2017/08/24/nyregion/showing-the-algorithms-behind-new-york-city-services.html) in New York City.  

Furthermore, open sourcing would provide a means for further testing the validity of our model. By making it available to others, we can rely on feedback from application to other places to see where there needs to be some tuning or clarification of the model. We have an idea of what the model looks like for Raleigh. It seems to make sense! But if we apply the same logic to Greensboro, Charlotte, or New Rocky Mount, does the output still make sense? Certainly this is something we can look into, but it would be even better if the people who work in those areas could run it with their data and offer feedback on what works and what doesn't.

Along the same lines, if we made it available on GitHub or some other code sharing platform, there is the possibility that we could get contributions from others who might be able to offer enhancements either to the model's analysis, performance, or usability. I'm currently the only person working on writing code for this project. I also know that I'm not always going to have the best solution to problems. I may not even recognize that there is a problem! By getting the model to a place where we can open source it, I think we'll be positioned to make this model accessible for a wider audience and also get some fresh eyes and ideas about how to improve it.
