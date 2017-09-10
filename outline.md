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

### Why an experience-based model?

Raleigh is a city that loves its parks, so much so that it is sometimes described as "a city within a park". Massive population growth over the past 30+ years has meant the parks system has had to grow as well. Helping to inform where our department acquires and develops property has been a level of service measure from 1917 that states "The area of parks and other public grounds within the city apparently presents the most satisfactory basis for computing the relation of population to recreational areas." In short,level of service is the population per acre of park land.

This measure has some shortcomings. First, it looks at the city as a whole and thus ignores the possibility that park amenities might be unevenly distributed. Second, it is a measure that is good for comparing level of service against other cities, but not for understanding level of service throughout our city. Our overall level of service compared to Charlotte, Wilmington, or Greensboro doesn't mean anything to the citizen whose taxes pay for our parks but is better served by Cary or Wake Forest.

This sort of course grained model wasn't really cutting it. So the Experience Based Park Access Model was developed to help address some key issues:

- Need to generate performance measures related to level of service
- Help target improvements to existing parks and greenways
- Help determine where to add new parks or develop existing park land
- Identify areas for land acquisition 
