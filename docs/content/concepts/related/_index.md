+++
title = "Related Projects"
weight = 205
toc = true
+++

There are a number of related projects in the project GitHub respositories, I'll call out a few key ones here:

## Choria Plugins

A number of Ruby based plugins are maintained in the [Choria Plugins](https://github.com/choria-plugins) organisation, these provide features such as Package, Service and Puppet management.  Many of them are installed by default when you install Choria but it's worth a check what else is there.  They are all distributed as [Forge Modules](https://forge.puppet.com/choria).

## Stream Replicator

Choria uses technology from [NATS.io](https://nats.io) in it's Network Broker but we also use the [NATS Streaming Server](https://github.com/nats-io/nats-streaming-server) in various situations.  The [Data Adapters](../../adapters/) supports bridging Registration and Choria Replies onto a NATS Streaming service.

You might have multiple data centers and want to transport these registration data to a central location in a way that is resilient to network outage and would support building multiple caches of data in multiple locations with different freshness cadences. You can also subscribe entirely different kind of processor for the data and each processor can consume the data it's own pace.

This is a key component to be able to build scalable asynchronous REST systems, schedulers and more.

The [Choria Stream Replicator](https://github.com/choria-io/stream-replicator) is the tool to achieve this and other tools mentioned below are developed to be compatible with data flows managed using it.

## Choria Embeddable Backplane

In a modern containerised world the use for a general purpose orchestration server like the main Choria Server is a bit limited, if you write your Microservices in Go though you can use the [Choria Embeddable Backplane](https://github.com/choria-io/go-backplane) to gain Circuit Breakers, Health Checks and Emergency Shutdown features that live on the Choria Broker Network where you can manage these Microservices using the CLI, Ruby API, Go API or Choria Playbooks.

Tools like the Stream Replicator and Prometheus Streams will feature this Backplane to manage their internals.

## Promethes Streams

Prometheus is a very flexible and scalable monitoring system but it has a very unfortunate Pull based system that requires vast amount of network ports to be opened between DCs. The [Choria Prometheus Streams](https://github.com/choria-io/prometheus-streams) project lets you poll in your remote DCs and have the metrics streamed over a NATS Streaming Server - and optionaly replicated using the Choria Stream Replicator.

Using this you can create a single pane of glass for multiple data centers.  It's not for all uses - in fact it has a very narrow focus, review it's README carefully before adopting it.
