# Feature Development

- Responsiveness
- Fit to app general design

## Async Execution

- Loading:
  - Async request may take a while, depends on the connection healthy of the user, which is unknown and unpredictable.
  - Make sure the user knows when something is loading
    - Loading Bar
    - Progress Bar
    - Some custom design
  - General loading bar vs per-Feature - per feature is preferred
- Failure
  - Show the user that something went wrong (the request has failed)
  - Make a friendly fail message. Be sure your client don't give a fuck about the error's stack trace, it just make the nervous.
  - Give the user the option to retry.
    - Of course, you can make a retry in the background (Please see Resilient Requests section), but in the end it can fail.
      - If the user makes a hard-F5 refresh to the browser - it's a failure
