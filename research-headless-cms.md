# Context based research 

**Main question**: how can the GGC app support content creation and management.

**Sub question**: Can a headless CMS be integrated in our microservice architecture.

## Can a headless CMS be integrated in our microservice architecture.

The main advantage of headless CMS compared to a CMS would be the ability to use multiple clients that use this data. This makes a headless CMS usable for our architecture. However not everything from an headless CMS can be integrated with an headless CMS. While multiple sources can use the HCMS the HCMS doesn’t integrate with anything. This means that ALL content needs to be stored in the HCMS for it to be manageable. This would split up the content management locations.

So to answer the question yes, but it won’t be able to take care of all our content management, so we would still need an extra implementation to manage other parts of the GGC. 

## Conclusion

For the best usability, and ability to manage all the content. An admin dashboard that integrated with the microservices so all the content of the site is in one location. This will however cost a lot more time.  