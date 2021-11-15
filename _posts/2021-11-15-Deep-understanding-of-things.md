---
published: false
---
## Having a deep understanding of things

Recently stumbled upon a Twitter post that went along the lines of: "how can infrastructure teams use most of the services offered by vendors like AWS without having a deeper understanding of how they are built internally?"

That got me thinking about the meaning of having a deeper understanding of the internals of something. I think this is actually different across the "infra people" and "regular developers" in the sense that infrastructure seems to be a somewhat special case of an abstraction that only (somewhat) recently has started to "bleed" into code with the recent approaches of infrastructure-as-code becoming more popular and containers becoming basically unnecessary _both_ in a local development context as well as a deployment context. I'll actually focus first on the topic from the perspective of a regular developer and later will touch upon it for the devOps people. 

I think that a certain level of abstraction is needed in order to be able to operate efficiently and be productive while working on modern web applications with common stacks such as Java or Python, for example.

At least in my personal experience, it's rare nowadays to have applications written in these languages that don't use a framework underneath to abstract way much of the details of network communication like sockets, packets or web servers. These concepts are integral to the development of these frameworks, but, to actually make use of them, you rarely need to know how to, for example, write a production ready concurrent web server.

It helps, and it can be seen as a requirement, to know that multiple requests can and are definitely handled concurrently by the server while the app is running, but, for the purposes of writing a Rest API and deploy it as a dockerized springboot app and having it running in a container, the details of how an embedded server like Jetty or Netty is written, are too low level, and, having to fiddle with such details in order to deploy your code, would, in my opinion, defeat the entire purpose of leveraging a framework in the first place. 
What's really important, is to be able to dive deep into the code and be able to understand things at least a level "lower" from the one you're operating at, but, that should be done only on demand and in the rare circumstances when there is really no other alternative. This is a skill that you can gain over time in a cumulative way by reading small bits of code from the libraries you're using and trying to understand how certain things are put together. Using Jackson to manipulate JSON? Invest some time to really grok how the serialization and deserialization processes work, and, you'll be able to more easily write custom mappers or extend existing ideas to better fit your model, etc, etc. 

The same kind of logic can be applied to infrastructure. If you invest in understanding how Docker works at least a level under the hood, how it isolates processes, how it exposes its running services to the host machine using a socket, and how it’s all wired together when running the services in a k8s cluster, you'll be able to understand 