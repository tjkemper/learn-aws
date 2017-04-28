# [Cloud Front](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)
* Global CDN
* Utilizes **Edge Locations**
* Improves latency
* High data transfer speeds

### Key features
* Dynamic content
* Supports POST/PUT and other HTTP methods
* Supports SSL
* Invalidation
* Wildcard CNAME support
* Enables domain apex support
* Custom error responses
* Enables low TTLs
* Support for cookies
* Support for query strings
* Enables device detection
* Geo targeting
* Origin Resource Sharing (CORS)

### [Types of Distributions](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-overview.html)

##### Web
* Static and Dynamic content over **HTTP** or **HTTPS**
* Apple HTTP Live Streaming (HLS)
* Can't serve Adobe Flash

##### Real-Time Messaging Protocol (RTMP)
* Stream media files using **Adobe Media Server**
* Must use **S3 bucket** as the origin

### Security
* CloudFront accepts requests over HTTP and HTTPS
* Can force HTTPS
* **Objects are encrypted in transit** - CloudFront uses HTTPS to retrieve objects from S3
* **Logs** - the object requested, date and time of request, edge location serving request, client IP, referrer, user agent
  * Specify name of S3 bucket to store logs in
* Enable **private content** feature to control who can download content from CloudFront *(signed URLs or signed cookies)*
  * Restrict access to objects in CloudFront edge caches
  * Restrict access to objects in your S3 bucket
* Only authenticated users can create, modify, or delete their own CloudFront distributions
* Requests are signed with an HMAC-SHA1 signature calculated from the request and the user's private key
* The control API is only accessible via SSL-encrypted endpoints
* **Durability** is provided by **S3 as the origin server** for CloudFront
* Private content is an optional feature that must be enabled when you set up your CloudFront distribution
  * Content delivered without this feature will be publicly readable by anyone
