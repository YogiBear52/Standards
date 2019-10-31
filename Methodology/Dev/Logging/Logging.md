# Logging

## Logging Architecture

- In most cases, using a service which is responsible for Logging is redundant.
  - Make a library/dll and use it from all of your services.
- Use a message broker/Queue/BUS tool to save the logs and process them.
  - Elastic and Kafka are just nice tools for visualizations.
  - Mongo is a nice place to store the Logs, thus in most cases, it doesn't worth the overhead maintainable and duplicated storage do save the logs both in ElasticSearch and Mongo
- Send logs only to one place (Mongo/Elastic/Kafka...)
  - There, process the logs as you want, and send them to other APIs (Email, Monitor dashboards, sms service..)
    - Calling other API's as a trigger to logs directly from servers is a Bad Practice.
- Don't log to the server's internal storage
  - You will never actually view this logs
  - Writing to disk a lot of logs is IO intensive and can decrease your server's performance
  - Will force you to use complex logging libraries
  - In containers world, internal storage is not even available.
- In some cases, when we are sending a lot of logs, we should implement a client-queue that will send batch of logs together to improve performance, ensure logs arrive and send while server is idle.
- TCP vs UDP
  - TCP can be very IO consuming if you have a lot of logs.
  - Consider using UDP in B-B if you can live with some logs drops.
- Keep only the important logs which will be used - Cost and Maintenance of huge data is not easy.
  - Categorize logs to Bushiness and Technical/Maintenance
- Standardize your logs format for easy exploration.
- Send Async Logs - Don't wait to the response. Maybe only in Development environment make the synchronous.

## What do we want to log ?

### Clint side

- All Errors

  - Listen to the browser's console
    - Some libraries can easily do it
  - All Http errors
  - Log as much as possible data of the errors (Stacktrace...)

- In each log include:
  - User Session ID (Per Tab)
  - Http Request ID
  - User details
  - Request total time elapsed (!!!)

### Server side

- Each request

  - Log it when the request is done
  - Log the Request info and Response info together - less complicated visualizations
  - Log request and response if you have enough storage
  - Time Trace
    - Log in an hierarchy data structure all measurements time that have been executed in this request
      - SQL query 1
      - SQL query 2
      - API A
      - API C
    - Send it to the client if security is non-issue
    - Now you can perfectly trace bottlenecks/ dying requests
      - Linear/Exponential Execution - number of queries to the same API is changing with different data and not O(1).
  - Server version (Assembly/Library version)
  - Logic environment version

- Server Cycle

  - On Start
  - On Stop
  - On Reset/Restart

- All Errors

  - Server Errors
    - Server is shutting down due to General Fatal Error
      - Make sure log has executed and sent before server is down
  - Request Error
    - All data available

- Technical Details
  - CPU
  - Number of threads
  - Memory taken by server + Total memory usage on container/VM

## Production Tests

- E2E and Integration tests will run on your production environment.
- They will produce logs as usual user, Make sure to log them as for a specific testing-user so you can identify them.
- Log all the tests results that will lated be used for Production-Health monitoring

## Business Logs

Hey lazy developer. Sometimes good KPI's logs(Business logs) are not so simple. Sometime they require to log a flow, a funnel and complicated scenarios. Treat it as a regular task, it may take you time to develop it.

### Tools

## ELK

- Not the best choice for storage, but Elastic as made good progress and now it can do well as a storage.
- Perfect for exploration.
- Be careful! Elastic is a beach. He may terrorize you with Schema Type Validation, especially when logs are unstructured(Errors/External API result).
- With ELK it's hard to know if and error occurred while ELK is processing your log. Since we usually make Async-Logs, we don't really know if the log has successfully written to Elastic or not.

## Mongo

- Good storage choice
- Nice tools for exploring specific things in the data.

## Kafka/ RabbitMQ / Other quere services

- Best choice to save the log there.
- Make use of these tools for processing, and handling a lot of data.
