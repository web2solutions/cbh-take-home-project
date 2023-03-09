# Ticket Breakdown

We are a staffing company whose primary purpose is to book Agents at Shifts posted by Facilities on our platform. We're working on a new feature which will generate reports for our client Facilities containing info on how many hours each Agent worked in a given quarter by summing up every Shift they worked. Currently, this is how the process works:

- Data is saved in the database in the Facilities, Agents, and Shifts tables
- A function `getShiftsByFacility` is called with the Facility's id, returning all Shifts worked that quarter, including some metadata about the Agent assigned to each
- A function `generateReport` is then called with the list of Shifts. It converts them into a PDF which can be submitted by the Facility for compliance.

## You've been asked to work on a ticket. It reads

**Currently, the id of each Agent on the reports we generate is their internal database id. We'd like to add the ability for Facilities to save their own custom ids for each Agent they work with and use that id when generating reports for them.**

Based on the information given, break this ticket down into 2-5 individual tickets to perform. Provide as much detail for each ticket as you can, including acceptance criteria, time/effort estimates, and implementation details. Feel free to make informed guesses about any unknown details - you can't guess "wrong".

You will be graded on the level of detail in each ticket, the clarity of the execution plan within and between tickets, and the intelligibility of your language. You don't need to be a native English speaker, but please proof-read your work.

## Your Breakdown Here

Before going to the main task of this challenge, I did create a pseudo version for a hypothetical `Human Resource` application.

Before to design this application, I made the following assumptions in terms of non-functional requirements:

### Assumptions

For this product, I'm assuming that we are the following technologies and principles:

- `Design approach`
  - Domain Driven Design
  - The Clean Architecture
  - Hexagonal Architecture
  - SOLID.
- `Language`: TypeScript
- `Database`: Agnostic, In Memory, Key/Value, NoSQL

### Implemented application

Please [check](https://github.com/web2solutions/cbh-take-home-staffing) the application code for further reference.

`https://github.com/web2solutions/cbh-take-home-staffing`

#### Project Structure

    .
    ├── ...
    ├── src
    │   ├── Domains
    │   │   ├── Facilities
    │   │   │   ├── Data Entity
    │   │   │   │   ├── IFacility.js
    │   │   │   ├── Data Model
    │   │   │   │   ├── Facility.js
    │   │   │   ├── Data Repository
    │   │   │   │   ├── FacilityMongoDB.js
    │   │   │   ├── Use cases
    │   │   │
    │   │   ├── Agents
    │   │   │   ├── Data Entity
    │   │   │   │   ├── IAgent.js
    │   │   │   ├── Data Model
    │   │   │   │   ├── Agent.js
    │   │   │   ├── Data Repository
    │   │   │   │   ├── AgentMongoDB.js
    │   │   │   ├── Use cases
    │   │   │
    │   │   └── Shifts
    │   │       ├── Data Entity
    │   │       │   ├── IShift.js
    │   │       ├── Data Model
    │   │       │   ├── Shift.js
    │   │       ├── Data Repository
    │   │       │   ├── ShiftMongoDB.js
    │   │       ├── Use cases
    │   │           ├── getShiftsByFacility.js
    │   │           ├── generateReport.js
    │   │
    │   └── Infrastructure
    │       ├── Persistence
    │       │   ├── BaseRepo.ts
    │       │   ├── InMemory.ts
    │       │   ├── Paging.ts
    │       │
    │       ├── Utils
    │
    ├── tests                   # Test files
    │   
    └── ...

### Ticket Breakdown

#### Ticket CBH-01 - Type: Epic

`Title`: Feature request | Add Agent custom ID to Agent Domain and `generateReport` Use Case.

`Description:`

    Currently, the id of each Agent on the reports we generate is their internal database id. We'd like to add the ability for Facilities to save their own custom ids for each Agent they work with and use that id when generating reports for them.

`Acceptance Criteria`:

New generated PDF reports must list out the Agent custom ID rather than the Agent ID.

##### - Ticket CBH-02 - Child of CBH-01

- `Title`: Update Domain component
- Update Agent Model - add customId

##### - Ticket CBH-03 - Child of CBH-01

 Update UI

- Agent - set custom ID

##### - Ticket CBH-04 - Child of CBH-01

Deploy - staging

- Fix staging data

##### - Ticket CBH-05 - Child of CBH-01

Production - Update agents - set custom ID

##### - Ticket CBH-06 - Child of CBH-01

Fix Production data - Shifts - add custom agent ID
