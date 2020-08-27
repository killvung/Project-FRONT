# Project-Front. 
FRONT is the personal system I came up to capture all my of fitness route data across multiple data sources. 
<img src="https://raw.githubusercontent.com/killvung/Project-FRONT/master/front_diagram_abstract.png?token=AB2UN7RVCMR5IIJ5HTEYSVC64LGAC"/>

FRONT is the abbreviation of 
- Fitness
- Routes
- Object
- Novel
- Technology

## Motivation:
I use multiple applications to track down my route related fitnesss activities (think of biking, running or walking). Later on, realizing the fact that all the information are spreaded across platforms, I found it difficult to analyze my overall performance for desired goals. For example, I want to trackdown the miles I have walked weekly; Has my running paces been improved over time; At one point I think of ploting all the dots from the routes on the map for the purpose of visualization. Given my education background and professional working experience, I can definitely implement a system myself to centralize all data and utilized them for further purposes.

## Get your hand dirty
Influenced by the hacker culture back in college, I wrote a [Proof of concept application](http://killvung.github.io/nuxt-front) to display all my walking routes in Austin area. Visitor can look at the heatmap to see the concentrated area for my walk, and display any five of the longest routes I have been so far.

Components: 
#### Client
- NuxtJS and VueJS for UI interaction
    -   To build a SPA with semi-complicated UI, Nuxt and Vue would be great choices compare to Nxxx and Rxxxx. 
- OpenLayer
    -   OpenLayer is used for displaying Austin map and plotting all the dots from the routes. 
#### Services
- Python backend with Flask web framework boilerplate (front-api) for save and get all fitness data (routes, distances...)
    - https://github.com/killvung/front-api
    - I used Python for the backend service for quick and easy purposes
- Apollo GraphQL Server (apollo-server) as a middleman to direct and easily manage complicated data 
    - https://github.com/killvung/express-apollo-server
    - Realizing there would be a lot of complex data fetched from the backend, I use Apollo GraphQL to dynamically adjust the data for different Vue components, without pick and choose through REST APIs.
#### Database
- Mongo Atlas to quickly stored raw data captured from datasources

## Retrospect
After drafting the first version of the system, I collected feedbacks from my friends and evaluate for potential features, as well as looking at the overall system for enhancement. This is Software Engineering, so there are million ways to "improve" it.

#### Too many hops
There are too many hops between client and servers. It's quite unnecessary to send data from python service to nodejs service then to the client. At first I thought Nodejs service is sufficient for reading and translating data from backend to frontend, but later on I realize all of the data don't need to render dynamically on the fly, so they can be static. Afterward, Python microservice can be repurposed to only resolving machine related tasks.

#### Frontend will be complicated
The current implementation for the frontend is fine, only if I want to render the map with routes on it. However, what if I later on decide to add more features? The logics would be extremly complicated.

To be continued...
