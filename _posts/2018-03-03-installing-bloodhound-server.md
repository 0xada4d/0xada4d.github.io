---
layout: default
title: "Installing Bloodhound Server"
date: 2018-03-03 12:00:00
tag: How_To
description: "Getting a Bloodhound server running using a Neo4j Docker image"
---

# Background

___

[Bloodhound](https://github.com/BloodHoundAD/Bloodhound) is an Windows Active Directory relationship visualization tool. From the [wiki](https://github.com/BloodHoundAD/Bloodhound/wiki):

> BloodHound uses graph theory to reveal the hidden and often unintended relationships within an Active Directory environment. Attack[er]s can use BloodHound to easily identify highly complex attack paths that would otherwise be impossible to quickly identify. Defenders can use BloodHound to identify and eliminate those same attack paths. Both blue and red teams can use BloodHound to easily gain a deeper understanding of privilege relationships in an Active Directory environment.

BloodHound is developed by [@\_wald0](https://twitter.com/_wald0), [@CptJesus](https://twitter.com/CptJesus), and [@harmj0y](https://twitter.com/harmj0y).

Bloodhound utilizes a [Neo4j](https://neo4j.com/) database to aggregate collected Domain information into an easy-to-understand, feature-rich graphical application. 

<figure>
![Image](/images/installbloodhound/gui.png)
<figcaption>*GUI-View of Ingested Domain Information*</figcaption>
</figure>