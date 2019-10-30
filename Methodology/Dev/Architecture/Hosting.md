# Hosting

- Environment Variables
  - Logical environment of the app (Production,Testing, Demo..)
  - Credentials
    - Since you should not check in your credentials to the source control, you need to pass them to you server with environment variables.
  - Don't confuse Environment variables with config file.
    - Don't overuse environment variables

## VM's

### NodeJs

- Put behinds a reverse proxy - Nginx
  - Handles all http traffic better
- PM2/forever
  - Helps the service restart with zero downtime
  - Makes a better use of the logical threads in your VM - It creates multiple processes/instances of your service.
