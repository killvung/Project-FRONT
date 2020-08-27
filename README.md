# Project-Front. 
FRONT is the personal system I created for capturing all of my fitness route data across multiple data sources. 
<img src="https://raw.githubusercontent.com/killvung/Project-FRONT/master/front_diagram_abstract.png?token=AB2UN7RVCMR5IIJ5HTEYSVC64LGAC"/>

FRONT is the abbreviation of Fitness (F), Route (R), Object (O), Novel (N), Technology (T). Meaning that it is a bleeding edge solution targed for tracking route related fitness activities (Run, Walk, Bike etc)

## Motivation:
I use multiple applications to record my fitnesss data. Realizing the fact that all of the information are spreaded across different platforms, it would be difficult to analyze my overall performance for desired goals. 
For example, the miles I have walked weekly; my running paces improvement over time; At one point I think of visualizing all the routes on the map. My education background and professional working experience can definitely help me out.

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

### Feedback
Even it's not something huge, I still have received multiple positive feedbacks from people, so I was quite motivated and decide to push the application to larger scale. (That's where the first sentence of this blog post coming from)

## Retrospect
After hacking out this web application, I have evaluated the system as a whole, and discovered several areas where I can improve it. (Thought there are million ways to "implement" and "improve" the solution in Software Engineering...)

#### Too many hops
There are too many hops between client and servers. It's quite unnecessary to send data from python service to nodejs service then to the client. At first I thought Nodejs service is sufficient for reading and translating data from the backend to the frontend, but later on I realize all of the data don't need to render dynamically on the fly, in another word they can be static. Afterward, Python microservice can be repurposed to resolve machine learning related tasks.

#### Frontend will be complicated
The current implementation for the frontend is fine, but only if I want to render the map with routes on it. However, what if I later on decide to add more features? The logics would be extremly complicated, hard to maintain and build. Can we break it down?

To be continued...
