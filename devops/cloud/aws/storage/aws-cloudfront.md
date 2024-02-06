# AWS Cloudfront

## Introduction

Amazon CloudFront is a web service that speeds up distribution of your static and dynamic web content, such as .html, .css, .js, and image files, to your users. CloudFront delivers your content through a worldwide network of data centers called edge locations.

When a user requests content that you're serving with CloudFront, the request is routed to the edge location that provides the lowest latency (time delay), so that content is delivered with the best possible performance.

That content is stored as cached data. After a set period of time, this data will expire, which means AWS Cloudfront doesn't provide durability of your data.

## Edge Locations

AWS edge locations are sites deployed in major cities and highly populated areas across the globe. They are not used yo deploy instances or storages, but to cache data and reduce latency for end user access.

For example, you may have your website hosted on EC2 instances or S3 within the Ohio region, with an associated CloudFront distribution. When a user accesses your website from Europe, they would then be redirected to their closest edge location in Europe, where cached data could be read of your website.

## Distribution Controls

CloudFront uses distributions to control which source data it needs to redistribute and to where. These distributions can be configured as one of two different delivery methods, via a web distribution or an RTMP distribution.

The web distribution can be used to distribute both static and dynamic content, in addition to using both the HTTP and HTTPS protocol.

If you need to add, remove or update objects, or provide live stream functionality on your website, then the web distribution will be able to provide this functionality for you.

The RTMP option should be used if your focus is to distribute streaming media with the Adobe Flash media service RTMP protocol.

The benefit of using RTMP distribution is that your end user can start viewing the media before the complete file has been downloaded from the edge location.