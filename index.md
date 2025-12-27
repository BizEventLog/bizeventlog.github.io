---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
title: Business-level observability made easy
---

![Image]({{ '/assets/image/open-source.svg' | relative_url }}){: width="150"}

Observability is the art to always know how your IT systems are doing.
But most solutions out there focus on the technical side,
like e.g. how many milliseconds it takes to load a certain web page.

So what if you get a call that a customer order was lost somewhere in
the dozens of systems involved in its processing? Can you enter the
customer number and see instantly the various steps that have been
executed? Is it easy to tell that a certain sub-system refused to
accept the order, perhaps because of a new validation?

Or do you have to sift through 15+ log files, cross-reference technical
IDs by hand, and manually search for the point where things went wrong?

If the latter sounds familiar, you should have a closer look at **BizEventLog**.

## How it works

The underlying principle of BizEventLog, as the name implies, is to look
at business transactions as a series of connected events. It is similar
to a business process model (think BPMN, ARIS EPC, etc.).

These events are linked via unique IDs and can be enriched with whatever
data makes sense for your busines. Those can be simple values like a
customer status, binary attachments like PDFs, or structured data like
JSON , XML, CSV, etc. And of course you can log individual steps like
"Customer status retrieved from XYZ = GOLD".

So for every step of the process you can easily see:

- With what data was it started?
- What happened along the way?
- Which sub-processes were triggered with what result?
- Relevant data, also for searching
- What data was returned to the parent process?

Together this allows you to quickly see what happened and react
accordingly.

The system is designed to support different types
of backends. So you can start with a plain file system, later
move to a relational database, or something else. No code changes
are required, just some configuration updates.

## Getting started

One of the big advantages of BizEventLog is that you can start without
any additional system. Because it supports multiple backend types
and one of them is the file system. So for small to mid-sized
deployments all data is simply written in files. With today's
SSDs this gets you surprisingly far, even without optimization
approaches like sharding.

At the moment only the file system store is implemented.
But going forward you can just as well use a database, transmit updates via a
message broker, etc.


<!-- 
### Example

So if a customer orders something, a business event "Customer Order"
is created and enriched with the metadata that are needed (example:
customer name and number). It also gets a unique ID (sometimes called
trace ID) that allows to tie all sub-activities to this order.

The next step could be an event "Credit Check". 
So a query needs to be sent to
a financial system. 
This event is child of
the top-level event "Customer Order" and linked to it. -->

