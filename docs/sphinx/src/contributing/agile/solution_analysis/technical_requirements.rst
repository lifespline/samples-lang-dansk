.. raw:: html

   <a href="https://github.com/lifespline/backlog.git"><img loading="lazy" width="149" height="149" src="https://github.blog/wp-content/uploads/2008/12/forkme_left_darkblue_121621.png?resize=149%2C149" class="attachment-full size-full" alt="Fork me on GitHub" data-recalc-dims="1"></a>

======================
Technical Requirements
======================

Read through the `technical requirements docs <https://lifespline.github.io/agile/src/development_flow/architecture_analysis.html>`_ for an introduction on how to iteratively contribute to the **technical requirements** of this project.

.. toctree::
   :maxdepth: 1

   technical_requirements/TR1
   technical_requirements/TR2.1
   technical_requirements/TR2.2
   technical_requirements/TR3.1
   technical_requirements/TR3.2
   technical_requirements/TR3.3
   technical_requirements/TR5
   technical_requirements/TR7.1
   technical_requirements/TR19
   technical_requirements/TR20

Requirements for BS1
--------------------

* ``R7.1: title``: The title of the task is persisted
* ``R7.2: content``: The content of the task is persisted
* ``R7.3: acceptance-criteria``: The acceptance criteria of the task is persisted
* ``R7.4: dor-definition-of-ready``: The DOR of the task is persisted
* ``R7.5: list-of-parents``:The list of parents of the task is persisted
* ``R7.6: list-of-children``: The list of children of the task is persisted
* ``R6.1: repo`` single line: string
* ``R6.2: branch`` derived, single line: string
* ``R6.3: title`` single line: string
* ``R6.4: parent`` derived, single line: string
* ``R6.5: content``: multiline.
* ``R6.6: dor-definition-of-ready``: multiline.
* ``R6.7: acceptance-criteria``: multiline.

.. code:: rst

   PS1: Tracking TODO tasks
   ┃
   ┗╸BS1: Add node with default properties
     ┃
     ┣╸AC11.1: title
     ┃ ┣╸R1: Network Rendering
     ┃ ┗╸R7.1: title
     ┃
     ┣╸AC11.2: content
     ┃ ┣╸R1: Network Rendering
     ┃ ┗╸R7.2: content
     ┃
     ┣╸AC11.3: acceptance-criteria
     ┃ ┣╸R1: Network Rendering
     ┃ ┣╸R6.7: acceptance-criteria
     ┃ ┗╸R7.3: acceptance-criteria
     ┃
     ┣╸AC11.4: dor-definition-of-ready
     ┃ ┣╸R1: Network Rendering
     ┃ ┣╸R6.6: dor-definition-of-ready
     ┃ ┗╸R7.4: dor-definition-of-ready
     ┃
     ┣╸AC11.5: list-of-parents
     ┃ ┣╸R1: Network Rendering
     ┃ ┗╸R7.5: list-of-parents
     ┃
     ┗╸AC11.6: list-of-children
       ┣╸R1: Network Rendering
       ┗╸R7.6: list-of-children

* ``R17: python get current directory``: get the current directory of where the task runner is executed from.
* ``TR18: CLI prototype to test network persistence interface``

Requirements for BS2
--------------------

TODO

Requirements for BS3
--------------------

TODO

Requirements for BS4
--------------------

TODO

Requirements for BS5
--------------------

TODO

Requirements for BS6
--------------------

TODO

Requirements for BS7
--------------------

TODO

Requirements for BS8
--------------------

TODO

Requirements for BS9
--------------------

TODO

Extra Technical Requirements
----------------------------

To each node:

* ``R8: attached-files``: Any attached files to the node, typically related to the node content, like images, diagrams, etc.
* ``R9: estimated-effort``: How much work this task is expected to require. It is required to come up with an unit for ``work``.
* ``R10: date-of-creation``: the date of creation of the node
* ``R11: date-of-completion``: the date of completion of the node
* edit:
    * ``list-of-parents``
    * ``list-of-children``
* get repo of parent node (if any) as to know from which branch to branch
* on removing node, decide what to do with the child nodes.
* ``R12: focus-toggle``: depends on user commitment for now, but it can be endlessly automated, this will be a roll-over feature, the more automated, the more effective. See the *pomodoro technique*.
* ``R13: dor-definition-of-ready``: individual checkboxes
* ``R14: acceptance-criteria``: individual checkboxes
* ``R15: due-date``: warnings on tasks density on the time neighborhood of this task.
* pretty print for activity in .rst

.. code:: rst

   ========
   Activity
   ========

   * ``title``: VSCode Shortcuts
   * ``parent``: ABH12NJ7
   * ``repo``: samples-vscode
   * ``branch``: vscode_shortcuts

   Content
   -------

   This is the activity description

   DOR - Definition Of Ready
   ------------------------

   * ``DOR.1``: multiline
   * ``DOR.2``: definition
   * ``DOR.3``: of ready

   AC - Acceptance Criteria
   ------------------------

   * ``AC.1``: multiline
   * ``AC.2``: acceptance
   * ``AC.3``: criteria

* ``R16: centralized database``: have a centralized database instead of local databases

==============================
Meeting Technical Requirements
==============================

* ``R2.1: Rendering Host``: The rendering requires a host that fetches the network data and renders it appropriately.
* ``R2.2: Network persistence interface``: There is a client that interfaces with the data persistency layer
* ``R3.1: Network Persistence``: The network must be persisted.
* ``R3.2: Network Editing``: The node and network information must be editable/removable
* ``R3.3: Persist multiline values and save formatting``: multiline values should be persisted.
* ``R5: Network Engine CLI Client``: A CLI client.


.. toctree::
   :maxdepth: 1

   technical_requirements/TR1
   technical_requirements/TR2.1
   technical_requirements/TR2.2



R2.2: Network persistence interface
-----------------------------------

The client is a node server handling requests to add, edit and remove data to a redis database. See sample to see how ``express`` and ``redis`` are satisfying this technical requirement.

.. code:: rst

   R2.2: Network persistence interface
   ┣╸✅ R3.3: Persist multiline values and save formatting
   ┗╸✅ R3.1: Network Persistence

✅ R3.1: Network Persistence
----------------------------

A dockerized redis database satisfies the requirement BY persisting data.

Definition of ready
~~~~~~~~~~~~~~~~~~~

* Validating POC: `Dockerizing a redis database <https://lifespline.github.io/samples-redis/src/samples_docs.html>`_

Acceptance Criteria
~~~~~~~~~~~~~~~~~~~

* script to launch the dockerized redis database
* add script to task runner to launch redis container
* add script to task runner to launch redis-server in container

QA Acceptance Criteria
~~~~~~~~~~~~~~~~~~~~~~

* documentation
* PR documentation

Pull Request
~~~~~~~~~~~~

`1 <https://github.com/lifespline/backlog/pull/1>`_

Requirements Dependencies
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: rst

   R3.1: Network Persistence
   ┗╸✅ R17: python get current directory

R17: python get current directory ✅
------------------------------------

Get the current directory from where the python script is running.

Definition of ready ✅
~~~~~~~~~~~~~~~~~~~~~~

* Validating POC: `Get current dir <https://github.com/lifespline/samples-python/tree/latest/samples/pwd_of_calling_process>`_ ✅

Acceptance Criteria ✅
~~~~~~~~~~~~~~~~~~~~~~

* get the current directory from where the python script is running. ✅

Release Commit
~~~~~~~~~~~~~~

`6d396fb9afdcef0178e0d3eef6646b788ea77215 <https://github.com/lifespline/samples-python/commit/6d396fb9afdcef0178e0d3eef6646b788ea77215>`_

✅ R3.3: Persist multiline values and save formatting
-----------------------------------------------------

A dockerized redis database satisfies the requirement BY persisting both values and files.

* Validated POC: `Dockerizing a redis database <https://lifespline.github.io/samples-redis/src/samples_docs.html>`_

R5: Network Engine CLI Client
-----------------------------

A python CLI client interacts with the node server. The python app uses ``invoke`` to simplify extending the CLI ops, which is basically a task runner. See sample to see how ``invoke`` and ``express`` are satisfying this technical requirement.

.. code:: rst

   R5: Network Engine CLI Client
   ┗╸R2.2: Network persistence interface


R4.1: Automated Architecture Infrastructure
-------------------------------------------

Docker compose will automate the deployment of the solution infrastructure. See `Docker Artek Samples <https://github.com/lifespline/samples-docker>`_ to see how ``docker-compose`` satisfies this technical requirement.

R4.2: Automated Architecture Infrastructure Pipeline
----------------------------------------------------

``Circleci``

R16: centralized database
-------------------------

The ``redis`` database can run locally at an early release, but it can become a centralized database in an AWS account.

R6.5: content
-------------

An editor opens a file where the following is written:

Example of (raw) .txt file for content (the formatting is optional)

.. code:: rst

   multiline
   content

R6.6: dor-definition-of-ready
-----------------------------

An editor opens a file where the following is written:

Example of (raw) .txt file for DOR (the formatting is optional)

.. code:: rst

   * ``DOR.1``: multiline
   * ``DOR.2``: definition
   * ``DOR.3``: of ready

R6.7: acceptance-criteria
-------------------------

An editor opens a file where the following is written:

Example of (raw) .txt file for AC (the formatting is optional)

.. code:: rst

   * ``AC.1``: multiline
   * ``AC.2``: acceptance
   * ``AC.3``: criteria
