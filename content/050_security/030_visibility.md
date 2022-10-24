+++
title = "Testing and Visibility"
weight = 30
+++



1. First lets try and attack our application with a XSS attack using the following URL  
`https://::makeid::.sales-public.f5demos.com/?a=%3Cscript%3Ealert(%27xss%27)`  
You will receive a response as seen bellow. Copy the support ID, this will allow us to understand why the request has beeמ blocked.

```
The requested URL was rejected. Please consult with your administrator.

Your support ID is 37e7688f-6fdd-404e-9f6d-3813f9dc5648

[Go Back]
```

2. Lets look at the logs and understand why the request has been blocked
![](/images/5/Slide3.PNG)