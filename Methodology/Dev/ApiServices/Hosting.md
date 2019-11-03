# Hosting

- Choose SLA for hosting services
  - High SLA for production and Pre-Prod Environments
  - Low SLA for development purposes in case of limit resources($$ dinero $$)
- Environment Variables
  - Logical environment of the app (Production,Testing, Demo..)
  - Credentials
    - Since checking in your credentials to the source control is not advisable , you need to pass them to you server with environment variables.
  - Don't confuse Environment variables with config file.
    - Don't overuse environment variables

## VM

### NodeJs

- Put behinds a reverse proxy - Nginx
  - Handles all http traffic better
- PM2/forever
  - Helps the service restart with zero downtime
  - Makes a better use of the logical threads in your VM - It creates multiple processes/instances of your service.
    - How ?? LB? NAT?

## Docker + K8S

## Docker

- OS
- Installations
- End to End Artifact (Infrastructure --> Code)

### BP

- MultiStage
  (?? Research more (Docker and Kubernetes))

## K8S

- Service Discovery
- LoadBalancer
- ApiGateway
- High availability
- Zero DownTime Deployment + Rolling Updates + Rollback
- Auto Scale

## Linux Vs Windows

VM OS can be whether Windows or Linux.

- Linux, Dah.
- Although Microsoft are trying really hard. Maybe soon finally Linux will have a competitor.

### Linux Distributions

(?? Research more)
