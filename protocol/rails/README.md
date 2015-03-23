Rails Protocol
==============

A guide for writing great web apps.

Set Up Laptop
-------------

Set up your laptop with [mac](http://www.carlosespejo.com/2015/01/12/kick-off-2015-with-a-fresh-install.html)
Set up PG with
[ubuntu](https://basecamp.com/2584938/projects/6492261/messages/37909485)
If you are new to rails env then go through [rails
tutorial](http://guides.rubyonrails.org/getting_started.html)


Git Protocol
------------

Follow the normal [Git Protocol](protocol/git/README.md).

Product Review
--------------

Follow the normal [Product Review
protocol](protocol/product-review/README.md).

Code Review
-----------

Follow the normal [Code Review guidelines](code-review/README.md). When reviewing others'
Rails work, look in particular for:

* Review data integrity closely, such as migrations that make irreversible
  changes to the data, and whether there is a related todo to make a database
  backup during the staging and production deploys.
* Review SQL queries for potential SQL injection.
* Review whether dependency upgrades include a reason in the commit message,
  such as a link to the dependency's `ChangeLog` or `NEWS` file.
* Review whether new database indexes are necessary if new columns or SQL
  queries were added.
* Review whether new scheduler (`cron`) tasks have been added and whether there
  is a related todo in the project management system to add it during the
  staging and production deploys.

Deployment
----------

View a list of new commits. View changed files.

    git fetch staging
    git log staging/master..master
    git diff --stat staging/master


What gets shipped into production & tagged

* Master branch should only contain code thats production ready.
* Your code must be environment aware ex: Rails has configurations for
development and production. Which makes sure that when your running
the project locally your not pointing to production databases, api's,
etc.
* Deployments will only pull from master and you only tag the master branch after
determining that the deployment was successful and production is not
broken.






Set Up Production Environment
-----------------------------

deployment tools will be provided soon by Carlos
