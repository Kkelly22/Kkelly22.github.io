---
layout: post
title:      "Breaking Down Storage Technologies"
date:       2019-06-09 21:36:24 +0000
permalink:  breaking_down_storage_technologies
---


Storage technology has evolved many times over through the years, and with this evolution comes a bigger variety of tools in our programming toolbox.  With this variety, though, comes decisions.  Which storage technology is right for my data?

To answer this question, we need to start by locking down our understanding of some of the more prominent storage technologies available today.  Once we understand the pros and cons of each technology, we have to understand the nature of our data.  Armed with this knowledge, we can design a data storage system that will mature gracefully with the evolution of the application itself.

1. **File-based storage**.  This method of storage has been around the longest, but limits our storage capabilities the most.  This type of storage involves defining a directory in which you'd like to store your data, and creating a file within that directory.  This file is clearly defined in terms of organization, access modes, record keys, and record lengths.  Reading through these files becomes a tedious task of spinning through each record, manually specifying the data you need to match on.  This is similar to jotting down information onto a piece of paper, putting the paper into a storage bin, and putting that bin in storage room.  When you need to find that piece of paper, you need to locate the bin within the storage room, and re-read the piece of paper to find the information you are looking for.  This method is straight forward, but not ideal for storing big data.  In order to store more data, we need to purchase more space.

Pros: Good for small data, secure
Cons: Limited scalability, slow performance, storage cost


2. **Relational Databases**.  This method of storage was developed in the 1970's, and offers many solutions to issues that arose with file-based storage.  Relational databases store data in tables and rows, and joins tables via a 'foreign key'.  These joined tables may store completely different data, but relate to each other on a certain level (like Books and Authors).  Using querying methods, this storage technique allows us to chain interconnected data in a relatively short amount of time to find a particular set of data.  A common way to query a relational database is to connect your preferred programming language to SQL querying methods using an ORM (Object-relational Mapping system).  In my experience, Ruby uses the ORM "Active Record".  

An example of a relational database is as follows:

BOOK TABLE:
BOOK ID
BOOK NAME
BOOK EDITION

AUTHOR TABLE:
AUTHOR ID
AUTHOR NA ME

BOOK_AUTHOR TABLE:
BOOK ID
AUTHOR ID

If I want to find a particular book by ID, all I need to do is employ a ".find" method which will utilize a SQL "SELECT" statement to find and return the data i'm looking for.  The use of SQL/ORMs make this method much more attractive than it's predecessor. 

Like with file based systems, this system also allows for vertical scalability.  I can continually purchase more storage space if I run out, however this is also not ideal for big data.  At a certain point, storage on a single server becomes costly and extremely latent.  

Pros: Good for frequent CRUD on a manageable level of consistent data
Cons: ORM Impedence Mismatching, must design referential integrity at its core

3. **Non-Relational Databases**.  This method of storage is the newest method of storage, and offers the most flexibility and scalability compared to both previously mentioned storage technologies.  A non-relational database stores data in a JSON document instead of tables and rows.  An example of a non-relational database object is as follows:

{"Books" : [ { Book ID, Book Name, Book Edition, Author ID, Author Name } , ... ] }

The object above represents a key/value JSON object.  This object is structured in a way where I can add more objects to the array containing my values, but I can also add more keys (representing new data needing to be stored) anywhere I need.  I can adapt to changing data demands very easily. 

This system also enables us to scale both vertically and horizontally.  I can purchase more storage on a single server like before, but given that my data is likely unstructured and does not rely on 'joins',  I can spread my storage across multiple servers.  This makes non-relational databases a great fit for big, unstructured data.

Pros: Scalability with big data, high throughput and low latency, easily accessible API
Cons: Extra processing efforts, lack of structure can become complicated to manage

*Summary*
Storage technologies differ widely in their composition and capability, and knowing the foundation of each type is the first step in being able to deploy them correctly.  Weighing the pros and cons of each method will help you decide which method is the right fit for your data.  Do you have a small amount of data with minimal and straight forward logical connections? Traditional file based storage may be the right fit.  Do you have a very structure, interconnected, and predictable set of data that will be constantly maintained?  A relational database may be the right choice.  Do you have a large amount of unpredictable data that will need to be elastic over time?  A non-relational database is definitely the best storage for you.

For a break down of ORM Impedence Mismatching and Referential Integrity, stay tuned for next weeks' blog.
