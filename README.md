# Project-Front
FRONT is the system I came up to capture all my fitness data across multiple sources. 

<img src="https://raw.githubusercontent.com/killvung/Project-FRONT/master/front_diagram_abstract.png?token=AB2UN7RVCMR5IIJ5HTEYSVC64LGAC"/>

FRONT is the abbreviation of 
- Fitness
- Replicate
- Operation
- Novel
- Technology

## Motivation:
I use multiple apps to track down my fitnesss activities, such as biking, running, walking, etc. Later on, due to the fact that all the information are spreaded across everywhere, I found it difficult to analyze my overall statistics for desired goals. For example, I want to trackdown how many miles I have walked weekly; Has my running paces been improved. I even want to plot all the routes on the map for visualization. Given my education background and professional working experience, I can definitely implement a system to centralize all the data from all datasources and utilized them for analytical purposes. 

## V1
Influenced by the hacker culture back in college, I wrote a [POC](http://killvung.github.io/nuxt-front) instantly to display all my walking routes in Austin great area and display the top 5 longest walking routes. 

Components: 
#### Client
- Vue front with Nuxt (nuxt-front)
- OpenLayer
#### Services
- Python backend with Flask web framework boilerplate (front-api) for save and get all fitness data (routes, distances...)
    - https://github.com/killvung/front-api
- Apollo GraphQL Server (apollo-server) as a middleman to direct and easily manage complicated data 
    - https://github.com/killvung/express-apollo-server
#### Database
- Mongo Atlas to quickly stored raw data captured from datasources

To build a SPA with semi-complicated UI, Nuxt and Vue would be great choices compare to Nxxx and Rxxxx. OpenLayer is used for displaying Austin map with plotted routes. Realizing there would be a lot of complex data fetched from the backend, I use Apollo GraphQL to dynamically adjust the data for different Vue components, without pick and choose through REST APIs. I used Python for the backend service to enable R&D from 3rd libraries, (science with data) ;-)

## Retrospect
After drafting the first version of the system, I collected feedbacks from my friends and evaluate for potential features. I also reviewed system components for better changes if possible. 

#### Too many hops
- First thing I noticed is that there are too many hops between client and backend. It's quite unnecessary to send data from python service to nodejs service then to client, instead the nodejs service is sufficient for reading and translating data from database. Indeed, the python backend service can be isolated from the rest of the components if I start implementing "science" features on it.
#### Frontend will be complicated
- The current implementation for the frontend will not be able to handle big and complicated UI logics (Dashboard, SideBar, Widgest...).

To build a scalable and functional system, one has to have a thoughtful idea for every system components, so I don't have to constantly go back and rewrote everything :-(
## V2
(On going)
