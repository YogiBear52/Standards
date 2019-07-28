# Methodology Metrics

- Velocity
- CycleTime
- TouchTime
- Efficiency (Touch/Cycle)
- Kanban column bottleneck
- Stories Size
  - Estimated Size
  - Actual Size
  - Estimated vs Actual
- Average/Mid Time to finish Story
- Number of stories with defined KPI
- WIP
  - Number of times WIP limit
  - WIP bottleneck
- Number of Commits Graph
- Commits sizes
- Ratio of Commits with Test files
- Bugs
  - How much time is taken to a bug to be fixed
    - After finding it
    - After committed to work on it
  - Bugs Trend
  - User Bugs
  - Only X bugs in backlog
- Technical Debt Trend
- Ratio of Features vs Bugs
- Ratio of (Features and bugs) vs Technical Debts
- Ambulances Trend
- Methodology Events
  - Retro times
  - Demo times

## Technologies

- Number of languages used
- Number of Big-Mid Frameworks/Libraries used
- For each Technology
  - Importance for project (1-10)
  - Complexity (1-10)
  - Learning Curve (1-10)
  - For each team member - Knowledge level (1-10)

## Project

- Timeline of project status [Production, POC,Maintenance, Failed]
- Estimated time left getting to the next status.

## Pipeline

- CI Total Time
- Full CI + Deploy to production Time
- Number of failure CI's over time

## APIs

- Number of APIs (More than X per module can be challenging)
- Per API:
  - Trust level (Feeling)
  - Status: In development / Deprecated / Not Supported
  - Critical level (For our business)
  - Test Coverage (1-10)
  - SLA Actual vs Expected
    - Latency
    - Request total time (Per query)

## Code

- Number of code lines (differ third-party code)
- Number of Services (See Microservice/Monolith trend)
- Test Coverage
- Code smells

## Errors

- Errors in production
  - Client errors (Http errors + regular exceptions from browser errors)
  - Services Errors
- Total number of Errors
- Total number of Unique Errors (Group by)
- How much time until Error has stopped (Tricky)

## Team Members

- Average team tech-experience
- Average management experience (Group + Team leader + Product)
- Missing Roles
- Productivity of each team member
