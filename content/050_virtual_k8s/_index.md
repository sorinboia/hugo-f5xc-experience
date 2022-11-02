+++
title = "Distributed Kubernetes"
menuTitle = "Distributed Kubernetes"
weight = 50
chapter = true
pre = "<b>5. </b>"
+++

F5 Distributed Cloud can provide a distributed Kubernetes environment where we can deploy our application containers in any of the F5XC Regional Edge or Customer Edge.  
This allows us to run our application code very close to the client and provide very fast responses.  
For our application the **Stocks** service is providing the current price of the crypto currency.
To ensure that the price that the client is seeing is the same as the backend and is not changing due to latency issues we are exposing the **Stocks** service both in the AWS site for use by the local services and at the same time deploy it on the London Regional Edge.

![](/images/diagrams/Slide7.PNG)