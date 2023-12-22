# Observability with Grafana

<a href="https://www.packtpub.com/product/observability-with-grafana/9781803248004?utm_source=github&utm_medium=repository&utm_campaign=9781803248004"><img src="https://github.com/PacktPublishing/Observability-with-Grafana/blob/main/Cover%20(1).jpg" alt="" height="256px" align="right"></a>

This is the code repository for [Observability with Grafana](https://www.packtpub.com/product/observability-with-grafana/9781803248004?utm_source=github&utm_medium=repository&utm_campaign=9781803248004), published by Packt.

**Monitor, control, and visualize your Kubernetes and cloud platforms using the LGTM stack**

## What is this book about?
This book provides a holistic understanding of observability concepts using the Grafana Labs tools, teaching you how to fully leverage the LGTM stack.

This book covers the following exciting features:
* Understand fundamentals of observability, logs, metrics, and distributed traces
* Find out how to instrument an application using Grafana and OpenTelemetry
* Collect data and monitor cloud, Linux, and Kubernetes platforms
* Build queries and visualizations using LogQL, PromQL, and TraceQL
* Manage incidents and alerts using AI-powered incident management
* Deploy and monitor CI/CD pipelines to automatically validate the desired results
* Take control of observability costs with powerful in-built features
* Architect and manage an observability platform using Grafana

If you feel this book is for you, get your [copy](https://www.amazon.com/dp/1803248009) today!

<a href="https://www.packtpub.com/?utm_source=github&utm_medium=banner&utm_campaign=GitHubBanner"><img src="https://raw.githubusercontent.com/PacktPublishing/GitHub/master/GitHub.png" 
alt="https://www.packtpub.com/" border="5" /></a>

## Instructions and Navigations
All of the code is organized into folders. For example, chapter3.
All the setup instructions can found in READMEs placed in the respective chapter folders
The code will look like the following:
```
histogram_quantile(
    0.95, sum(
        rate(
            http_server_duration_milliseconds_bucket{}[$__rate_interval])
        ) by (le)
    )
```

**Following is what you need for this book:**
If you’re an application developer, a DevOps engineer, a SRE, platform engineer, or a cloud engineer concerned with Day 2+ systems operations, then this book is for you. Product owners and technical leaders wanting to gain visibility of their products in a standardized, easy to implement way will also benefit from this book. A basic understanding of computer systems, cloud computing, cloud platforms, DevOps processes, Docker or Podman, Kubernetes, cloud native, and similar concepts will be useful.

With the following software and hardware list you can run all code files present in the book (Chapter 3-6).
### Software and Hardware List
| Chapter | Software required | OS required |
| -------- | ------------------------------------ | ----------------------------------- |
| 1-13 | Kubernetes v1.26 | Either Windows, macOS, or Linux with dual CPU |
| 1-13 | Docker v23 | Either Windows, macOS, or Linux with dual CPU |

### Related products
* AWS Observability Handbook [[Packt]](https://www.packtpub.com/product/aws-observability-handbook/9781804616710?utm_source=github&utm_medium=repository&utm_campaign=9781804616710) [[Amazon]](https://www.amazon.com/dp/1804616710)

* Becoming a Rockstar SRE [[Packt]](https://www.packtpub.com/product/becoming-a-rockstar-sre/9781803239224?utm_source=github&utm_medium=repository&utm_campaign=9781803239224) [[Amazon]](https://www.amazon.com/dp/1803239220)

## Get to Know the Authors
**Rob Chapman**
is a creative IT engineer and founder at The Melt Cafe, with two decades of experience in the full application life cycle. Working over the years for companies such as the Environment Agency, BT Global Services, Microsoft, and Grafana, Rob has built a wealth of experience on large complex systems. More than anything, Rob loves saving energy, time, and money and has a track record for bringing production-related concerns forward so that they are addressed earlier in the development cycle, when they are cheaper and easier to solve. In his spare time, Rob is a Scout leader, and he enjoys hiking, climbing, and, most of all, spending time with his family and six children.

**Peter Holmes** 
is a senior engineer with a deep interest in digital systems and how to use them to solve problems. With over 16 years of experience, he has worked in various roles in operations. Working at organizations such as Boots UK, Fujitsu Services, Anaplan, Thomson Reuters, and the NHS, he has experience in complex transformational projects, site reliability engineering, platform engineering, and leadership. Peter has a history of taking time to understand the customer and ensuring Day-2+ operations are as smooth and cost-effective as possible.

