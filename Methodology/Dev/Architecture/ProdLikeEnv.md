# Prod-Like Environment

Testing environment will be used to test the whole application just before deploying the new app version to production.

Simulating a Prod-Like environment is super important so we can experience the new version as our client will.

Doing so helps in finding production-unique bugs.

This environment must be nearly identical:

- Hosting
  - Same SLA for VMs, K&S
    - The only excuse not to do so is a money-resources consideration.
    - Don't pity for your hosting providers
  - Same Data Center
- DataBase
  - Use the same DataBase
    - Usually Database can provider logical separation(Schema- RDBMS, database - mongo ..)
    - Afraid to load your DB resources so it will badly effect the production performance?
      - Most modern DataBase can split resources well (CPU,RAM,STORAGE). You will use these resources in separate environments, so why not to combine them? + Some Databases can scale out easily
    - In case you manage to fuck-up the Database because of the tests running on it - Perfect! Awesome opportunity to track down the issue cause it - You don't want it to surprise your one day when traffic is high on production.
- Network and Security
  - On the same subnet, router and firewall
  - Apply the same security policy
- External APIs
  - This is the hardest part.
  - Use their production APIs
    - Some API's letting you create a test-user. Consider it in complicated situations.
  - What if we insert/modify data some external APIs? We will trash their data..
    - Per situation. Per test case
  - As a last resort, you can replace an API with a fake one.
