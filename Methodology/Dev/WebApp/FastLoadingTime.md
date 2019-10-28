# Fast Loading Time

According to recent studies, 47% of visitors expect a website to load in less than 2 seconds, and 40% of visitors will leave the website if the loading process takes more than 3 seconds.

- CDN - (Content delivery network). A CDN takes a website’s static files – such as CSS, images and JavaScript – and delivers them on servers that are close to the user’s physical location. Because servers are closer to the user, they load more quickly.
- 61% of a website’s page weight on a desktop computer is images
  - Lower size and Quality of the image without the user to notice.
  - Compress Images
- Cache Static information to reduce number of initialz requests
  - Local cache
  - Browser DB for complex
- Enable Http Keep-Alive for connection pooling.
  - Not all Http clients enable it by default
  - Listen to timeout because client assumes connection is open and ready.
  - [More Info](https://lob.com/blog/use-http-keep-alive)
- Compress bundle
  - Static compression - High ratio
- Highest version of Http
  - Http 2.0
- Use Webpack
  - Optimize chunks so the app will not be fully downloaded in the beginning
