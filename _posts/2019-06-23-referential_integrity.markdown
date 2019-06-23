---
layout: post
title:      "Referential Integrity"
date:       2019-06-23 23:08:50 +0000
permalink:  referential_integrity
---


Referential integrity - what is it and why is it important?

Let's look at a formal definition first.  If you look up the term on IBM, you'll find

> Referential integrity is the state of a database in which all values of all foreign keys are valid. A foreign key is a column or a set of columns in a table whose values are required to match at least one primary key or unique key value of a row in its parent table. A referential constraint is the rule that the values of the foreign key are valid only if one of the following conditions is true:
They appear as values of a parent key.
Some component of the foreign key is null.

This sounds a little complex, but it's intuitive.  In layman's terms-* if you refer to something, that 'something' needs to exist*.  

But let's take a step back.  First and foremost, this term applies to data management, and we manage data through CRUD operations (Create, Read, Update, Delete).  This means we need to have referential integrity each time we **create** data, **update** data, and **delete** data.  That way, when we **read** data, we know the data maintains referential integrity and is completely valid.  *We can rely on the data to be correct*.

**Create**.  When we create data, we are inserting it into the database.  So this can be thought of as the insert rule.  To follow the insert rule, if you attempt to insert data with a foreign key, that foreign key MUST be a non-null valid that links up to a key in a parent table.

**Update**.  The update rule. When updating data, if the update in question changes the value of the parent key, then this change must be reflected in each "child".  This is often referred to as a cascading update.

**Delete**.  The delete rule. When deleting data, you cannot delete a record in a parent table without deleting all of it's "children".  This is often referred to as a cascading delete.

We can summarize these rules into an intuitive set of best practices:
1) If you insert a parent/child relationship into the database, the child must exist.
2) If you update a parent who has children, the children must be updated too,
3) If you update a child who belongs to a parent, the parent must know of this update and be updated as well.
4) If you delete a parent who has children, each child must be deleted as well

If we follow the referential integrity constraints during each CRUD operation, our database will be accurate.
