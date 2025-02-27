# Image scanning<a name="image-scanning"></a>

Amazon ECR image scanning helps in identifying software vulnerabilities in your container images\. The following scanning types are offered\.
+ **Enhanced scanning**—Amazon ECR integrates with Amazon Inspector to provide automated, continuous scanning of your repositories\. Your container images are scanned for both operating systems and programing language package vulnerabilities\. As new vulnerabilities appear, the scan results are updated and Amazon Inspector emits an event to EventBridge to notify you\.
+ **Basic scanning**—Amazon ECR uses the Common Vulnerabilities and Exposures \(CVEs\) database from the open\-source Clair project\. With basic scanning, you configure your repositories to scan on push or you can perform manual scans and Amazon ECR provides a list of scan findings\.

## Using filters<a name="image-scanning-filters"></a>

When an image scanning type is configured, you may specify that all repositories be scanned or you can specify filters to scope which repositories are scanned\. Image scan filters are supported for both the basic and enhanced scanning types\.

When a filter is specified, a filter with no wildcard will match all repository names that contain the filter\. A filter with a wildcard \(`*`\) matches on any repository name where the wildcard replaces zero or more characters in the repository name\.

The following table provides examples where repository names are expressed on the horizontal axis and example filters are specified on the vertical axis\.


|  |  prod  |  repo\-prod  |  prod\-repo  |  repo\-prod\-repo  |  prodrepo  | 
| --- | --- | --- | --- | --- | --- | 
|  prod  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes | 
|  \*prod  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-no.png) No |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-no.png) No |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-no.png) No | 
|  prod\*  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-no.png) No |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-no.png) No |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes | 
|  \*prod\*  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes | 
|  prod\*repo  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-no.png) No |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-no.png) No |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-no.png) No |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonECR/latest/userguide/images/icon-yes.png) Yes | 

**Topics**
+ [Using filters](#image-scanning-filters)
+ [Enhanced scanning](image-scanning-enhanced.md)
+ [Basic scanning](image-scanning-basic.md)