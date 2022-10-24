+++
title = "Testing API Security"
weight = 50
+++

First we need to verify that the previously defined policy is working as expected


1. Browse to `https://::makeid::.sales-public.f5demos.com/notanactualpage`  
You should be able to recive all the relevant HTML, JS, CSS and have rendered the 404 page.

2. Browse to `https://::makeid::.sales-public.f5demos.com/v1/notanactualapi` 
The request will be blocked with a 403 message and a **support ID**. Copy to the clipboard the **support ID**.

```
The requested URL was rejected. Please consult with your administrator.

Your support ID is 687cd41c-2435-4b95-8008-e26f637e0d33
Error 403 - Forbidden
F5 site: ams9-ams

[Go Back]
```

3. Lets look at the logs and understand why the request has been blocked
![](/images/5/Slide7.PNG)