---
layout: default
title: Identifiers
date: 2022-12-14 23:50:45 +0100
nav_order: 1
parent: Fundamentals
grand_parent: Systems
permalink: /identifiers.html
---

# Identifiers

Identifiers are unique values that are used to identify and distinguish different entities within a system. For example, a customer ID or a transaction ID. Identifiers are important because they provide a common reference point that can be used to link data between different systems.

For example, if you are integrating a customer relationship management (CRM) system with an e-commerce platform, you might use a customer ID as an identifier to link customer records between the two systems. This allows you to seamlessly combine and analyze data from both systems, and to provide a more comprehensive view of your customers and their interactions with your business.

In addition to linking data between systems, identifiers are also important for ensuring the accuracy and integrity of your data. For example, if you are using a transaction ID as an identifier, you can use it to verify that the data for a particular transaction is correct, and to detect and prevent duplicates or errors.

## Bad or inconsistent identifiers - a world of pain

Bad identifiers can cause problems because they can lead to confusion, errors, and data inconsistencies. For example, if an identifier is not unique, it may be assigned to multiple entities, which can cause confusion and data corruption. Similarly, if an identifier is not consistent, it may be assigned different values for the same entity, which can lead to data inconsistencies and errors.

The consequences of getting identifiers wrong can be severe, as it can lead to a range of problems and issues. For example, it can make it difficult to accurately and reliably link data between different systems, which can hamper data analysis and decision-making. It can also make it difficult to maintain the integrity and accuracy of your data, which can impact the quality of your products and services.

> To take a SaaS example. If we have a customer named `Acme Ecommerce` , with the account number `1234`. If the CRM system uses `Acme Ecommerce` as the identifier for this customer, and the financial customer reporting system uses `1234` as the identifier, it may be difficult to link the data for this customer between the two systems. This could lead to problems such as:
>
> Inaccurate data: If the data for `Acme Ecommerce` in the CRM system is not accurately reflected in the financial customer reporting system, it may be difficult to provide accurate and reliable reports to `Acme Ecommerce`, which could impact the quality of the service provided to him.
>
> Inconsistent data: If the data for `Acme Ecommerce` in the CRM system is not consistent with the data in the financial customer reporting system, it may be difficult to provide a comprehensive and consistent view of `Acme Ecommerce`'s interactions with the business, which could impact the customer experience and the overall effectiveness of the business.
>
> Data errors: If the data for `Acme Ecommerce` in the CRM system is not properly linked to the data in the financial customer reporting system, it may be difficult to detect and correct errors in the data, which could impact the quality and reliability of the data.

## Important properties of identifieers

To avoid problems, identifiers should have the following attributes:

- **Uniqueness:** Identifiers should be unique, so that each entity is assigned a distinct identifier that cannot be confused with any other identifier.

- **Consistency:** Identifiers should be consistent, so that the same entity always receives the same identifier, even if it is accessed or modified by different systems or users.

- **Stability:** Identifiers should be stable, so that they do not change over time. This ensures that the identifier remains valid and can be used to consistently and accurately identify the entity that it is associated with.

- **Generality:** Identifiers should be general, so that they can be used across different systems and contexts. This allows the identifier to be used as a common reference point that can be used to link data between different systems.

- **Robustness:** Identifiers should be robust, so that they can withstand errors and errors. For example, if an identifier is generated using a hash function, it should be resistant to collisions and other forms of corruption.

## Examples for identifiers

Identifiers can take many different forms, depending on the specific system and context in which they are used. Some examples of identifiers in SaaS-related systems include:

- **Company/Contact/Deal IDs:** In a CRM system, a record ID might be a combination of the customer's first and last name, with a unique number appended to it (e.g., `john_smith_1234`). In HubSpot each object consists of a unique number. In HubSpots case that number is unique for each object type but not unique across objects.

- **Subscription IDs:** In a SaaS subscription platform, a subscription ID might be a combination of the subscriber's name, the subscription plan, and the start date (e.g., `john_smith_enterprise_2022-12-14`).

- **User IDs:** In a social media platform, a user ID might be a combination of the user's username and the platform's domain name (e.g., `john_smith_twitter.com`).

- **Transaction IDs:** In an e-commerce platform, a transaction ID might be a combination of the date, time, and transaction amount (e.g., `2022-12-14_10-01-23_99.99`).

- **Hashed IDs:** Hashes are often used as identifiers because they are _unique_ (or it is exceedingly unlikely that they are duplicated), _immutable_ and fixed in length, and _secure_ as the enable verifying the integrity of data without exposing the data itself. See [how identifiers are created](/identifiers.html#how-identifiers-are-created) for more detail

- **Event IDs:** In an event management platform, an event ID might be a combination of the event name and location, with a unique number appended to it (e.g., `company_holiday_party_new_york_123456`).

## How Identifiers are created

There are several different systems for creating and allocating identifiers, each with its own rationale and advantages. Some common systems for creating identifiers include:

- **Sequential numbering:** In this system, identifiers are assigned in a sequential manner, with each new identifier being assigned the next number in a sequence. This system is simple and easy to implement, and it ensures that each identifier is unique. However, it can be difficult to maintain the sequence if identifiers are deleted or reassigned, and it may not be well-suited to systems with large numbers of entities.

- **Hash-based identification:** In this system, identifiers are generated by applying a hash function to a combination of the entity's attributes. This ensures that the identifier is unique and deterministic, and it allows for easy verification of the entity's attributes. However, it can be difficult to map the identifier back to the original entity attributes, and the length of the identifier may be longer than with other systems.

A typical hash looks like a string of characters, often composed of letters and numbers. The length of the hash will depend on the specific hashing algorithm being used, but common lengths include 32, 64, or 128 characters. Here is an example of a hash:

`efd3b43e8c3b53f9c0db43d9f8c7b039`

This is a 32-character hash generated using the MD5 hashing algorithm. Hashes can be generated using a variety of different algorithms, each with its own set of characteristics and trade-offs.

- **Random number generation:** In this system, identifiers are generated by generating a random number and checking that it is not already in use. This ensures that the identifier is unique, and it allows for a high degree of flexibility in terms of the length and format of the identifier. However, it can be difficult to ensure that the random number generator is truly random, and there is a risk of collisions if the number of entities is large.

## You can't identify what isn't there - data modelling

In some cases, a system may not have an appropriate model of the reality it is trying to represent. This can happen when the system is not designed or modeled carefully, and may lead to errors, inconsistencies, and difficulty in using the data effectively.

A system that conflates the representation of _customers_ with _subscriptions_ would treat a _customer_ and a subscription as the same thing. This would make it difficult to distinguish between _customers_ and _subscriptions_, and to track data about each entity separately.

When working in RevOps you will encounter this situation again and again.
Companies or accounts are conflated with subscriptions are conflated with customers or legal agreements and you run into situations such as two companies merging but retaining separate subsriptions.
Another example is _contacts_ being treated as _leads_ or _opportunities_. The contact representing the person is marked as a sales qualified lead (SQL) once. How do you handle that contact becoming a SQL a few years later?

Systems like your CRM tend to come with out-of-the-box representations that you start working with and over time start working around.
Be careful of blindly inheriting these abstractions or bastardising them for other uses.
