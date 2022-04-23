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
*pg 29-*

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
  - 


## 4: Requirement Gathering

## 5: High-Level Design

## 6: Low-level Design

## 7: Development

## 8: Testing

## 9: Deployment

## 10: Metrics

## 11: Maintenance

## 12: Predictive Models

## 13: Iterative Models

## 14: RAD

