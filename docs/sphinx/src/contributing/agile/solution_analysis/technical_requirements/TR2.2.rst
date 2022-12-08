.. raw:: html

   <a href="https://github.com/lifespline/backlog.git"><img loading="lazy" width="149" height="149" src="https://github.blog/wp-content/uploads/2008/12/forkme_left_darkblue_121621.png?resize=149%2C149" class="attachment-full size-full" alt="Fork me on GitHub" data-recalc-dims="1"></a>

====================================
TR2.2: Network persistence interface
====================================

About
-----

There is a client that interfaces with the data persistency layer.

Solution
--------

The client is an ``express`` server handling requests to add, edit and remove data to a redis database.

Definition of ready
-------------------

* Validating POC: `handle requests to a dockerized redis database with node <https://lifespline.github.io/praxis-advanced/src/samples_docs.html>`_

Acceptance Criteria
-------------------

* dockerized express server
* handle GET request to dockerized redis database
* handle POST request to dockerized redis database
* handle DELETE request to dockerized redis database
* handle PUT request to dockerized redis database
* task runner task to setup dockerized express server
* test requests with CLI app prototype (``invoke``) that opens editor to buffer file that is persister in the redis database. The app prototypes what will be the CLI app for the end user.

QA Acceptance Criteria
----------------------

* documentation
* PR documentation

Pull Request
------------

`CODE <https://github.com/lifespline/backlog/pull/CODE>`_

Requirements Dependencies
-------------------------

* ``TR2.2: Network persistence interface``
    * ✅ ``TR3.3: Persist multiline values and save formatting``
    * ✅ ``TR3.1: Network Persistence``
