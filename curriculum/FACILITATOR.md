# 401 Advanced Javascript

## Daily Lecture Schedule and Overview

The facilitators folder in each day contains information for the instructional staff. Your daily lecture schedule should follow a format similar to the following, adjusting for your class needs.

* :05 - Introduction, Welcome, Announcements
* :20 - Lightning Talk (1 Student per day)
* :20 - Concept Review / White Board / Warm-Up
* :15 - Code Review
* BREAK
* :30 - UI, Design, CS Concepts or Code Review Continuation
* :30 - Lecture on the new concept of the day
* BREAK
* :55 - Live Code Demo
* :05 - Lab Preview

**Hour 1**

Use the first hour to start the day cleanly with announcements, code review and optional extra material. 

If you are having your class do lightning talks (optional), then start the day with this, and allow a few minutes for feedback, but limit this block to about 20 minutes..

Additional time is allotted for 20 minutes or so of optional "get ready" exercises such as ...

 * Q&A (Quiz Style)
 * Live white-board session with one student. 
 * Demonstrating (or better - pair programming with a student or TA) one of the daily/weekly warm-ups from the post-grad roadmap
 
 All are valuable, and should be rotated by the instructor based on the needs and rhythm of the class.
 
 Complete the first hour with some basic code review (you can go deeper in the next hour if you need to).
 
 Keep the pace of this first hour up. Switching gears between those different "segments" is great to keep students attention.

**Hour 2**

During the 2nd hour, use the first half hour to either finish code review or introduce a new CS or UI concept as a short change of pace. 

This is a great time to squeeze in some CSS tricks, review recursion or reinforce anything that the students need clarification on. 

Close the hour with a solid presentation of the new material and topic for the day. This is where you'll do drawings, share a powerpoint and do your more traditional "lecture"

Basic code demos to support some of the high level items are ok in this segment, but generally, try and keep this high level, using imagery and live data/sites to illustrate the **concept**

**Hour 3**

Finish the day with a live coding demo that supports the class topic with much more granularity and sets the students up for executing their lab.
    * Demo should be supportive of the day's principle concept
    * Go over the assignment(s) and set expectations


## Course Content

### Block 1 - Javascript Fundamentals
The theme for the block is to spin the students up on fundamentals of the language and to get them ready for the rhythm that is 401 Javascript

This week, they will see TDD for the first time and start to use CI (Travis) and CD (Heroku) as a part of their daily routine.

They will NOT be doing daily Warm-Ups, Practice or Design Challenges for the first 5 classes (they start on Class 06). That said, the instructor should begin each of the first 4 classes with what would be the daily warm-up and practice exercise (and post the code). This sets the stage with the students for how they should be preparing to work each day, and also provides them code as guidance as they (inevitably) fumble through the first set of warm-ups

* Class 00/01:
  * On nights and weekends, this will actually be on a Saturday
  * This is a long day, and a brain melter. Lots of demos, lots of good video. Defintely do each of the sections in managagle chunks, record and label each video for easy access in  youtube.
  * Plan for a 6 hour session.
    * Campus Coordinator will do a kick-off
    * Everyone does their personal pitch/introduction
    * Lab, DSA, Warm-Up, Design Repo Build-outs
    * Complete a full lab to serve as the "Gold Standard"
    * Complete CI/CD/TDD Demo
* Class 02: Working with objects (constructors, factories, classes) at a deep level.
* Class 03: Async - event loop, callbacks, promises, async/await
* Class 04: Buffers and file read/write
* Data Structure: Linked Lists
* Project: Bitmap Transformer
  * Traditionally, this is a beast. Having some experience with buffers on Class 04 should ease that part of the burden, but this is still a monster.
  * Students must work in pairs to get it done.


### Block 2 - API Servers
The principle focus in this block is REST, from both sides of the equation. We will be building out an extensible REST API Server, while at the same time building out some client applications that are meant to consume that API.

We'll also get into mongo and data modeling in NOSQL databases. This is the main topic on one day, but remember that data storage can happen 100 ways, mongo being one. Dive more into why an API needs the data layer vs the layer itself.

The students primary focus will be in building the API itself, but their daily labs will include client applications and sibling servers (in various states of operation and disrepair) that they will need to ensure that they are keeping track of.

The principle takeaways need not only be **WHAT** REST is, but **WHY** its important and how it gets used in real world applications.

The api server we build is designed to be extensible. Start building it out with a separate router for each data model. Once that gets annoying, genericize it by making the model dynamic.  In this way all of the common routes that do the same things no matter what the model is, can be done in a single API router. This is a big concept that really sells the idea of keeping things DRY and on point.

`app.get('/api/v1/:model', (req,res) => {});`

Being comfortable with tools like `httpie` and `RESTy` (our Postman clone), debugging on the server, has to be paramount as they get ready for daily dev life. Make sure that you are using the debuggers as often as you can to cement that process in.

We have spent a lot of time in the first two blocks of the course talking through modularization, single responsibility, etc.  For the end of week project, the students will revisit Book App from 301 (provide them the day 14 solution code) and make it modular and awesome.

* Data Structure: Stacks and Queues
* Project: Book App

### Block 3 - Auth/Auth
This block takes the API server to 11. These 4 classes layer on the concept of authentication and authorization.

For the first 2 classes we focus on "getting you logged in", first with basic (username+pw) authentication and then using OAuth. We will be creating a middleware component to do this, so that you can protect a route

`app.get('/thing', auth, (req,res) => {});`

The OAuth demo is a long one, and the students lab is going to be their most ambiguous one since bitmap. They will be assigned (randomly) and OAuth provider and need to research, implement, document and then present to the class the next day a report of how it all went. They'll need to read docs and be ok with failing. A good way to start that lab is to tell them that their boss is giving them 24 hours to research a possible solution and evaluate it for usability, reliability, ease of implementation, etc. That way, if it's not 100% complete, their reporting of it details why.

Using OAuth as a guide, we have the students complete a solid token based authentication system.  Both with disposable and renewable JWT tokens as well as a more permanent "API Key" system (where JWTs are stored and re-usable)

We finish out with implementing an Access Control system. More advanced middleware that you can use to protect any route with, so that a user must be both logged in AND possessing the right permissions to access a resource.

`app.post('/thing', auth('write'), (req,res) => {});`

The block-end project is a fully baked, authenticated, dynamic modeled, completely tested API server. This is their "Golden Server" that will serve as a primary takeaway from the course and will also power much of the 2nd half (React) projects.

* Data Structure: Trees
* Project: Complete API Server

### Block 4 - Realtime
This block deals with event driven programming at a core level.  We begin the week with a simple lab that uses events within itself to signify that "jobs are done" rather than call a series of functions.

Students have done some event driven apps before (jQuery) but not at a business level. This will be their first time actually writing and working with multiple servers, clients, and seemingly disconnected codebases.

The block will move from internal events, to using TCP and Socket Events, and finishing with Socket.io bridge events between server and web clients. The week ends with building a small scale RabbitMQ Clone.

The message here needs to be "Real Time" doesn't just mean "Chat" but large scale problem solving. Lots of real world examples this week really sells the message.

* Data Structure: None
* Project: Q Server

### Block 5 - Mid-Term Project

### Block 6 - React Basics
Focus on getting the students to "start thinking in React", which really means architecting what is a component, what is shared between, where can we (or should we) share state.

From a coding/concept standpoint, the takeaway from this block must be an understanding of how to manage component and application state, how to pass state and methods to child components through props, and how things generally connect.

**State Management** - We will only be using native app/component state.

**Build and Deploy** - We will only be using `create-react-app` during this first block.

Have a daily exercise where the students are physically drawing the application architecture, component and data flow, and events. Having solid footing on how a React app is constructed and and connected within itself is critical leading in to the more advanced concepts.

Spend a lot of time in Class 27 talking through test procedures, examples, and proving that React tests can work at Travis. Close with deploying your apps to an AWS Bucket directly and also with an automated build using the .yml script.

The project at the end of the block is a rebuild of City Explorer. In 301, they built the back-end. Now, they will refactor the front end from jQuery+Handlebars into React. Fun!

* Data Structure: Sorting Algorithms
* Project: Refactor RESTy from Vanilla/jQuery into React

### Block 7 - Hooks, Context, CRUD, Auth, Realtime

**State Management** - In this Block, we introduce Redux and manage state globally for all classes.

**Build** - Use an 'ejected' `create-react-app` this block for final deployment. 

For the end of block build, students will create a CMS that re-involves their API server from earlier in the course. This is a big build that has them getting a list of models, a list of records for each model and then CRUD on each record.

* Data Structure: Hash Tables
* Project: Refactor RESTy from Component State to Context/Hooks

### Block 8 - Redux State Management

**State Management** - In this Block, we introduce both the Context API and Hooks and manage state using these methods instead of Native State or Redux.  This is all about teaching the students about choice and choosing the best state manager for the task at hand.

Once Authentication and Login are wired in, we will revisit Real-Time with socket.io and start creating a chat-like application that requires a login to function and operate.

**Build and Deployment** - This block, we'll be using a custom `webpack` configuration instead of `create-react-app`

For the end of block build, students will work locally (not in code sandbox) and will be required to use webpack instead of create-react-app. The course configs folder contains a working config.  Students should use that as a reference.

The build itself uses socket.io to create an app that uses the Q server from the first half of the course and builds a live front-end dashboard. The API server should already be hooked up to post messages to the Queue on all write activity. (If not, then this should be done in class). The class should re-do their UML of that API and the Q server to cement how it works. On the React side, they'll be connecting to the Q server using the "subscriber" library that they wrote for that Project in block 4. Using it, their app can now "see" all database activity in real time. The project is to connect all of those pieces and make a living dashboard with a killer UI that operates in real time.

* Data Structure: Graphs
* Project: Refactor RESTy from Context/Hooks into Redux

### Block 9 - React Native and UI Frameworks
The last block traditionally is difficult. Students have their eyes on their final exam, final projects and graduation.  For that reason, this week is light and fun.

First, we do a couple of classes in React Native, just to whet their appetite and give enough of a running start to allow them to build a mobile app. The first of these classes centers on "how to be a native app dev (tools, etc)" and the second class has them building actual phone apps.

We end the last 2 days with a research project. Assign the students a framework (Vue, Angular, Ember, etc) and have them spend 2 days building an app and then composing a report/presentation to the class with their findings.

This is educational and great practice, but also a light touch way to end the course on a really high note.

* Data Structure: Final Exam
* Projects: RNA Apps and UI Framework Reports

### Block 10 - Final Project

