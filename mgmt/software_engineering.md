# Software Engineering

*Beginning Software Engineering - Rod Stephens*

## 1: Software Engineering From 20,000 Feet
*pg 3-11*

**Basic Software Engineering steps**
- Rqeuirements gathering
  - what the customers want/need
  - good for keeping project development on track (prevent feature-creep)
- High-level design
  - decisions about project architecture, organization, and tools that will help satisfy customer requriements
- Low-level design
  - information for developers that guide developers in implementing high-level design
- Development
  - implemnting the low-level design 
- Testing
  - testing ensures the program is working as intended
  - helps find bugs, since the longer a bug remains undetected, the harder it is to fix
    - this is because things are connected and dependent on each other; so if theres a bug in one part, then there will be many other bugs as a result of dependencys
- Deployment
  - releasing software for customers use
- Maintenance
  - enhancements, bug fixes, improvements, etc
- Wrap up
  - evaluate the project and decide what went right and wrong, which is useful for the future

**How bug fixes can cause other bugs**
- it could be that a bug fix is incorrect or the fix breaks another piece of code that depended on the original buggy behavior
- tests can prevent bug fixes from causing other bugs by making sure everything works as it should

**Why detecting mistakes early as possible is important**
- mistakes can propagate and cause more mistakes since processes are dependent on each other

## 2: Preparations, tools, documents
*pg 15-28*

- Tracking changes in documentation allows you to have historical information that can give the what, when, and why on project decisions and materials
- Document management
  - ex: requirement document, use cases, design documents, test plans, user training materials, etc
  - such documents are "living" in that it evolves over time as development progresses
    - ex: customers changing requirements
- Change control
  - it is useful to approve and reject changes to prevent project development from getting out of control
- document control system
  - system that prevents concurrent changes to the same document 
  - includes these features
    - sharing document for people to view and edit
    - restricting edits to only one person at a time
    - ability to fetch most recent version of a document
    - ability to fetch a specific version of a document (by date, version number, etc)
    - ability to compare differences between versions
  - document control system can provide historical information on changes for project members to see who and what behind the changes throughout development
- One main purpose of documentation is to ensure project members are in sync and heading in the same direction
- one way to store historical documentation materials is via email and cc-ing materials to an account dedicated to the project

## 3: Project Management
*pg 29-52*

**Purposes of management**
- setting, tracking, and meeting project goals
- keeping team members on track

**Executive Support**
- a software project must have consistent executive management support to be successful
- Executive champion/ sponsor is the high-ranking executive who supports your project
- Executive support ensures that a project gets the resources it needs to be successful
- Helps allow project to continue if it encounters unexpected setbacks
- Protects project from corporate politics and attempts of cancellation
- defines business case and gives guidance on high-level issues
- usually stays out of the way and mainly monitors the project

**Project Management**
- highest ranking member of the project team
- monitors project progress to ensure that its on track, time-wise and feature wise
- meets with customers and other stakeholders to verify if the project meets their requirements

**PERT charts**
- Program Evaluation and Review Technique
- a graph that uses nodes and links to show the precedence relationships among the tasks in a project
  - by precedence, it means that tasks that must be done first for other tasks to be worked on
- types of PERT charts
  - AOA
    - Active on arrow
    - arrows = tasks
    - nodes = milestones
  - AON
    - activity on node
    - arrows = precedence relations
    - nodes = tasks
- Building an AON PERT chart
  - list tasks in the order that they must be performed
  - pg 35-38 has screenshots of PERT charts

**Critical Path methods**
- longest possible path in a task network in a PERT chart
- if any task in critical path is delayed, then project will also be delayed by the same amount of time
- lets you plan around tasks that may or may not delay project completion deadlines

**Gantt Charts**
- bar chart that shows a schedule for a collection of related tasks
- horizontal bars indicate task durations

**Estimating time**
- PERT and Gantt charts can be used to estimate project duration time
- COTS (commercial off the shelf) applications can be used to avoid building a project
- prior experience can help improve time estimates
- to account for unknowns, expand task estimates

**Risk Management**
- idenitification of risks, impacts, and possible responses
- To manage risk for tasks, these should be determined:
  - familiarity with doing task (if unknown task, then there might be unknown risks)
  - severity of task (can it be cancelled and pushed to be worked on later?)
  - consequences (will problems in the task affect other tasks?)
  - work-arounds (possible, alternative solutions to the tasks)


## 4: Requirement Gathering
*pg 53-87*

**Requirements**
- features that your aplication must provide
- gathered from customers
- guides development and helps keep things on track
- should be clear, unambigous (define unambigous terms like "best" or "fastest"), consistent with each other (no conflicts or contradictions), verifiable (able to be determined if requirement is met or not), avoid using of imprecise adjectives
- MOSCOW - must, should, could, wont

## 5: High-Level Design

## 6: Low-level Design

## 7: Development

## 8: Testing

## 9: Deployment

*pg203-215*

- Deployment
  - process of putting the finished application in the user hands
  - implementation, installation, and release

**Scope**
- number of users and sice of the application
- projects with smaller scope is easier to deploy
- when considering deployment, scope of the project is important to consider

**Planning deployment**
- list out steps for deployment
- list out the ways the steps could fail
- describe actions to take if any failure occurs
- creating a rollback plan to undo all the steps taken in deployment to restore project to its initial state

**Cutover**
- process of moving users to the new application
- One way to manage cutover is to release a new version of an application and letting users download it
- There are several ways to minimize disruptions when moving users to new application
  - staged deployement
  - gradual cutover
  - incremental deployment
  - parallel testing

**Staged development**
- helps reduce failures by using a staging area to practice deployment and test for any issues and fix any problems

**Gradual cutover**
- where some users get the new application while others continue to use the older version
- allows to test for issues while minimizing the number of users who get potentially disrupted
- might complicate things since users will be using different applications and therefore their work may be incompatible
  - ex: database items in the older format may be incompatible with the new version

**Incremental deployment**
- releasing new system features to users gradually
- doesn't work with monothlic applications since you can't just install part of a system
- works will with iterated development approaches like agile

**Parallel testing**
- where you have some users use the new version with the old one

**Deployment tasks**
- things to deal with for large deployment
  - physical environment (place, equipment, tools, etc)
  - hardware
  - documentation
  - training
  - database (migrations, backups, etc)
  - software (other software that interacts with your software)
  - own software

**Deployment mistakes**
- assuming everything will work
- having no rollback plan
- not allowing enough time to handle unexpected problems
- not knowing when to give up and try again later
- skipping staging
- deploying everything at once
- using unstable environment
- setting an early point of no return where you can't roll back your changes


## 10: Metrics

## 11: Maintenance

## 12: Predictive Models
*pg 265-283*

**Model approaches**
- development models help solve particular problems that may arise in software development 
- usually focuses on particular rules and methods

**Predictive and adaptive model**
- predicitve development model is where you predict in advance what needs to be done and then implement it
  - the downside is that you might not know what needs to be done or the requirements might change
  - good for when project is small and you are familiar with what needs to be done
- adaptidve development model lets you respond to changing requirements by periodically reevaluating the project and changing things if necessary

**Waterfall**
- predictive model where you do each step in the project development process (ex: requirements, design, implementation, etc) before moving on to the next step
- alot of time is spent on the planning and design parts
- works well if requriements are known in advance and wont be changing

**Waterfall with feedback**
- this variation of the waterfall model lets you move backwards one step
- development becomes harder if you move multiple steps

**Sashimi**
- AKA waterfall with overlapping phases
- variation of waterfall where steps are allowed to overlap
- For instance, you can define requriements while designing the project
- allows for people with different skills to focus on their specialities without waiting for others or for the steps of the project development cycle to complete
- allows for ability to research (deep dive) into particular topic for some requriement
- allows for later steps to modify earlier steps

**Incremental waterfall**
- where you have series of separate waterfalls (cascades) that ends with a delivery of some increment version of an application
- each increment includes more features than the previous one
- similiar to adaptive development models
- still a predictive model because changes are limited to the waterfall predictions and takes longer than stages in most adpative models

**V-model**
- waterfall where tasks are separated into two categories (each in one side of the V)
  - tasks on the left side break application down from highest conceptual level into more detailed tasks (decomposition)
  - tasks on the right side works project back to high conceptual level via testing, validation, etc (intergration)

**Software development life cycle (SDLC)**
- covers all the tasks that go into software engineering from start to finish
- waterfall is one version of SDLC
- SDLC steps
  - initiation - where customer, executive champion, or software manager comes up with the intial idea
  - concept development - where the concept or initial idea is explored and refined with more details
    - project defiition, fealsiblity analysis, cost benefit analysis, risk benefit analysis
    - this is where project can be cancelled without too much loss, unlike in the other steps of SDLC
  - preliminary planning - this is where the technical lead and project manager begin planning and assigning project members and creating estimates
  - requirements analysis -  this is where requirement documents are created (uml diagram, protoptypes, business rules, etC)
  - high-level design - this is where major systems, database needs, workflow and so on is defined
  - low-level design - this is where details are fleshed out for programmers to implement
  - development - this is where work is done to fulfill project
  - maintenance - this is where enhancements, bug fixes, etc is applied
  - review - this is where project development is assessed using the metrics utlized during development and reviewed to determine improvements in the future
  - disposal - this is where application is removed and data is archived or protected

## 13: Iterative Models
*pg 283-303*

**Iterative vs predictive**
- shortcomings of predictive models
  - predictive models can handle small changes, but not big changes well
  - alot of time in predictive model is spent planning what to do
  - predictive model require detailed requirements at the beginning of the project; otherwise, you can't plan and do task scheduling
- iterative models address the shortcomings of predictive models by building project incrementally
- iterative model iterations have small duration cmopared to predictive model project
- iterative model handles fuzzy requirements by allowing to work on the knowns and handling unknowns later

**Iterative vs incremental**
- project development can be iterative and not incremental by doing work that doesn't add new features but rather improves existing ones
- fidelty - completeness of feature
- Describing development models via fidelty
  - predictive - provides all features at the same time with full fidelity
  - iterative - initially provides all features, but at low (yet usable) fidelity; later iterations provide higher and higher fidelity until its completed
  - incremental - provides fewest possbible features to make MVP, but all features are present with full fidelty; later versions add more features at full fidelty
  - agile - provides fewest posible features at low fidelity; later versions improve fidelity and adds new features

**Prototypes**
- simplified model that mimics the part of the application that needs to be built
- doesn't need to work the same way as the final version nor implement all the features
- can be used to get feedback on requirements from customers
- horizontal prototype - demonstrates many project features, but with little depth
- vertical prototype - provides alot of depth to only a few features
- throwaway prototype - temporary prototype whose code is not used
- evolutionary prototype - prototype that has new features added to it until it morphs into the fnished application
- incremental prototype - where you a collection of prototypes are built that separately demonstrate the finished application features, eventually becoming the finished application itself
- downfall of prototype
  - narrowing vision - prevents identificiation of alternative solutions to a problem
  - customer impatience - if customer sees prototype, they might think that the finished product is close to completion when it may not be
  - raised expectation -  prototype may demonstrate features that won't be included in the application 

**Spiral**
- uses risk-driven approach to help project teams decide on what development approach to take for various parts of a project
- phases
  - planning phase - determine objectives of the current cycle and its alternatives and contraints
  - risk analysis phase - determine biggest risk factors that could prvent achieving cylce's objectives
    - resolve risks and build a prototype
  - engineering phase - use prototype to evaluate solution
  - evaluation phase - evaluate progress and get feedback; redo spiral dev cycle to fix whaterver problems that may remain
  - ![image](https://user-images.githubusercontent.com/14286113/164953426-20aee90a-556d-4d5c-95b2-34374b80056b.png)
- final trip aroudn sprial is implementing the application
- not a series of waterfall models drawn in a spiral since spirals can be done concurrently
- considered to be the most flexible development approache
- can be complicated and not worth the effort for low-risk application
- mainly good for large, high-risk projects

**Unified process**
- iterative and incremental development framework that can be customized for business/ project needs
- four phases:
  - inception - coming up with project idea, providing business case, identifying riks, providing general schedule and goals
  - elaboration - project requrirements and identifying and planning for risks
  - construction - implementation
  - transition - deployement and maintaence
  - prdouction - where users use the proeduct
  - dispoal - removing application
- can be complicated

**Rational unified process**
- uses same 4 basic phases of unified process
- difference is the tools to make using the process easier
  - artifact templates, document production and sharing, change request tracking, visual modeling, performance profiling, etc
- artifact - final or intermediate result that is produced by project

**Cleanroom**
- emphasisez bug prevention
- very test-driven
- lots of statistical quality control and testing
- requires math

## 14: RAD
*pg 303 - 355

**Overview of development models other than RAD models**
- Iterative models (ex: iterated waterfal and unified process)
  - allows you to change project course of direction if it goes off track or if requirements change over time
- Prototyping
  - helps ensure application meets customer requirements
- unified process
  - ensures project succeeds and manages risk effectively

**RAD development models**
- helps increase development speed so applications are completed quickly and delivered to customers asap
- one of the main principles is that requirements change often
  - problem with non-RAD projects is that by the time project is finished, it most likely won't satisfy customer needs since reqruiements can change
  - iterative development approaches can keep project on track, but not good enough since iteration duration is very lone
- RAD uses iterations that are short in duration
  - iteration is applied to the entire software development process, not just the programming part
- features small teams, repeated testing and constant integration and short iterations

**James Martin RAD**
- Four phases
  - requriements planning
  - user design (ie prototyping)
  - construction (development)
  - cutover (deployment)
- the user design and construction phases overlap

**Agile**
- agile is more like guidelines for software development
  - not a methodology
- documentation and modeling should be not excessive
- planning is good but doesn't work in environment of changining requirements

**Agile Techniques**

- Self-organizing teams
  - team that has the flexibility and authority to find its own methods for achieving its goals

- communication
  - frequent and continuous customer communication to keep project on track
  - Usually, technical lead or project manager is the point of contact for customers and programming team
  - many meetings for developers

- incremental development
  - agile projects are iterative and incremental
  - iterations are short
  - iterations incorporate every development step
    - so iterations are like mini-projects

- focus on quality
  - development must be high quality in that there should be no bugs or major issues
  - this is because iteration cycles are short so not much time can be spent of bug-fixing
  - some techniques like TDD and pair programming helps achieve high quality code

**Extreme Programming (XP)**
- Pair programming
  - where two or more programmers work on a piece of code together
  - one is the driver and controls the keyboard and explains what they are programming
  - the others are observers that review each line of code as its typed and makes sure the code makes sense and does what its supposeed to do
    - also considers possible improvements and changes

- XP roles
  - customers - defines requriements, verifies application meets user needs, and provides frequent feedback to keep development on track
  - tracker - monitors team member progress and provides useful metrics
  - programmer - defines application architecture and writes code
  - coach - helps team work effectively, self-organize, and use good XP practices
  - tester - helps customer write and perform acceptance tests for use cases; looks for missing requirements and holes in design
  - admin -  sets up an maintains team member environment and workspace

- Practices
  - having customer on site
  - planning
  - standups
  - frequent small releases
  - simple designs
  - deferring optimizations
    - important to first make project work, and then worry about optimizations later
  - refactoring only when necessary
  - giving ownership of code
  - using coding standards
  - promoting generalization
    - where everyone knows the general gist of every piece of the system
  - pair programming
  - constant testing
  - continuous integration
  - TDD
  - intuitive domain/ metaphors (making it easier for users to understand applicaiton)

**Scrum**
- roles
  - product owner: customres, users, and stakeholders
    - this is where user stories come from which makes up the product backlog
  - team member - those who build the application
  - scrum master - ensures team follows good Scrum practices, leads meetings, removes obstacles, etc
- scrum sprints
  - series of timeboxed incremental iterations, typically weeks or month long
  - result of sprint is a potentially shippable increment (PSI)
- burndown charts are used to measure progress
  - shows amount of work reminaing, plotted over time
- velocity
  - represents the amount of work team can perform during a sprint

**Lean**
- idea is to keep applications as lean as possible
  - meaning that nohting should go into an application without a good reason
- Principles
  - eliminate waste
    - unclear requiremnts (either clarify them or eliminate them)
    - unnecessary features and code
    - unnecessary repetition
    - unnecessary meetings 
  - deferring decisions until you know enough to make them intelligently
  - deliver quickly
  - build knowledge

**Crystal**
- family of development methodologies that feature the word crystal and project size in its name
- _details skipped_

**Feature driven development**
- designed to work with large teams
- focuses on application features, adding them through iteration
- _details skipped_

**Agile unified process**
- agile version of the unified process
- _details skipped_

**Disciplined Agile Delivery**
- aka DAD
- people first
- learning oriented
- hybrid of many agile development models

**Dynamic systsems development method (DSDM)
- _details skipped_


**Kanban**
- _details skipped_
