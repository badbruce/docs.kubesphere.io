---
title: "Project Gateway"
keywords: 'kubernetes, docker, helm, jenkins, istio, prometheus'
description: ''
---

The gateway in the project is a [Nginx Ingress Controller](https://www.nginx.com/products/nginx/kubernetes-ingress-controller). KubeSphere has a built‑in configuration for HTTP load balancing, called Routes, that defines rules for external connectivity to services. Users who need to provide external access to their services create a Route resource that defines rules, including the URI path, backing service name, and other information. Set the gateway can then automatically program a frontend load balancer to enable Route configuration.

## Set Gateway

1. In the current project, select **Project Settings → Internet Access**, click **Set Gateway**, which is the gateway entry for the route, and each project has a separate gateway entry.

![Set Gateway](https://pek3b.qingstor.com/kubesphere-docs/png/20190320183638.png)

2. Select the type of gateway in the pop-up window, and support the following two access methods:

> - NodePort: The gateway can access the service through `{$IP}:{$Nodeport}`.
> - LoadBalancer: The gateway can be accessed through an external network IP.

### NodePort

3. Click **Save** to create the gateway. The following method selects the NodePort mode. The two ports generated by the left node port are the HTTP protocol port and the HTTPS protocol port. 

![NodePort Gateway](https://pek3b.qingstor.com/kubesphere-docs/png/20190320185455.png)

The external network can pass EIP:NodePort or Hostname:NodePort to access the service, such as:

- Access via EIP:、
   - `http://139.198.0.20:30798`
   - `https://139.198.0.20:31279`


- Access via Hostname set in the route rules:
   - `http://demo.kubesphere.io:30798`
   - `https://demo.kubesphere.io:31279`


![View the gateway](https://pek3b.qingstor.com/kubesphere-docs/png/20190320185722.png)

### Load Balancer

It requires to install the cloud provider plugin if using the Load Balancer that is connected to the cloud provider. The [QingCloud Controller Manager Plugin](https://github.com/yunify/qingcloud-cloud-controller-manager) is still in the development stage and will be coming soon. You will be able to use Load Balancer to expose the service to external network after it gets ready.

![Load Balancer](https://pek3b.qingstor.com/kubesphere-docs/png/20190320190356.png)