---
layout: post
title: Versioning of Serializable Obejects
wordpress_id: 486
wordpress_url: http://www.hijava.org/?p=486
date: 2009-09-17 21:08:36.000000000 +08:00
---
When Java objects use serialization to save state in files, or as blobs in databases, the  potential arises that the version of a class reading the data is different than the version  that wrote the data.

Versioning raises some fundamental questions about the identity of a class, including what constitutes a compatible change.A compatible change is a change that does not affect the contract etween the class and its callers.

This section describes the goals, assumptions, and a solution that attempts to address this problem by restricting the kinds of changes allowed and by carefully choosing the  mechanisms.The proposed solution provides a echanism for “automatic” handling of classes that  evolve by adding fields and adding classes. Serialization will handle versioning  without class-specific methods to be implemented for each version. The stream format can be traversed without invoking class-specific methods.

更多参照：Java™Object Serialization Specification 
