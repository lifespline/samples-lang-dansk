.. raw:: html

   <a href="https://github.com/lifespline/backlog.git"><img loading="lazy" width="149" height="149" src="https://github.blog/wp-content/uploads/2008/12/forkme_left_darkblue_121621.png?resize=149%2C149" class="attachment-full size-full" alt="Fork me on GitHub" data-recalc-dims="1"></a>

==================
Behaviour Analysis
==================

Read through the `behaviour analysis docs <https://lifespline.github.io/agile/src/development_flow/problem_analysis/behaviour_analysis.html>`_ for an introduction on how to iteratively contribute to the **behaviour analysis** of this project.

Problem/Solution Analysis
-------------------------

Read through the `problem/solution analysis docs <https://lifespline.github.io/agile/src/development_flow/problem_analysis/problem_solution_analysis.html>`_ for an introduction on how to iteratively contribute to the **problem/solution analysis** of this project.

A network graph with nodes representing tasks and edges representing to which tasks a task relates to, should:

* provide a way to PS1 by having nodes persisted and representing the tasks;
* it should provide a way to understanding the context of each task by displaying the edges between nodes (recursively, it will show how that task is contributing to something the agent can relate to primarily);
* it should provide a way to prioritize tasks by checking the timeline for each node;
* it should provide a way to track the progress of tasks by seeing how many child tasks/nodes have been finished;

Universal Behaviours
--------------------

The following behaviours enable globally the solution to all the problem statements (meaning all the problem statements solutions depend on this behaviour):

.. toctree::
   :maxdepth: 1

   behaviours/BS0


PS1: Tracking TODO tasks
------------------------

The following behaviours enable ``PS1``:

.. toctree::
   :maxdepth: 1

   behaviours/BS1
   behaviours/BS2
   behaviours/BS3

BS1: Add node with default properties
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

About

   Adds a new node with a template.

Acceptance Criteria (Customer)

    * the node has the properties:
        * ``AC11.1: title``: the title of the task
        * ``AC11.2: content``: a description of the task
        * ``AC11.3: acceptance-criteria``: the criteria for the task to be considered completed
        * ``AC11.4: dor-definition-of-ready``: what must be in place for the task to be ready to be worked on
        * ``AC11.5: list-of-parents``: the tasks this task is related to, or the tasks this task helps accomplishing
        * ``AC11.6: list-of-children``: the tasks related to this, or the tasks that help accomplishing this task
    * the task is created and shown

.. image:: ../../../../static/img/BS1.png
    :width: 400
    :alt: Behaviour 1 Specification

.. _BS2:

BS2: Edit node properties
~~~~~~~~~~~~~~~~~~~~~~~~~

SPEC

    Edit node properties

    * ``title``
    * ``content``
    * ``acceptance-criteria``
    * ``dor-definition-of-ready``

.. image:: ../../../../static/img/BS2.png
    :width: 400
    :alt: Behaviour 2: SPEC

TEST SPEC

    * ``title``: verify that the edited title of the task is persisted
    * ``content``: verify that the edited content of the task is persisted
    * ``acceptance-criteria``: verify that the edited acceptance criteria of the task is persisted
    * ``dor-definition-of-ready``: verify that the edited DOR of the task is persisted

.. _BS3:

BS3: Remove node from graph
~~~~~~~~~~~~~~~~~~~~~~~~~~~

SPEC

    Remove node from graph

.. image:: ../../../../static/img/BS3.png
    :width: 400
    :alt: Behaviour 3: SPEC

TEST SPEC

    * verify that the node was removed
    * verify that the node's children are now orphans
    * verify that the node's children haven't lost any nodes

.. _BS4:

BS4
~~~

SPEC

    Have intuitive visualization of the backlog nodes.

.. image:: ../../../../static/img/tasks-network-graph.png
    :width: 400
    :alt: Intuitive visualization of the backlog nodes

TEST SPEC

    * verify that the chosen visualization renders successfully
    * vefify that the chosen visualization is intuitive

.. _task_context_behaviour:

Understanding the need/the context for each task
------------------------------------------------

Create a **first set of primary nodes** representing **what the agent likes/wants to do with his life**. All subsequent nodes should derive from these, or from a child of these - recursively.

BS5
~~~

SPEC

    Items derive from:

    * ``creativity``
    * ``passion``
    * ``performance``
    * ``power``

    Discarded items derive from:

    * ``physical-stimuli``
    * ``memory``: past reality
    * ``imagination``: alternate reality
    * ``emotion``: strong physical sensation prompting action (fear, anger, etc.)
    * ``thought``: new perspective on reality, typically a solution or hint
    * ``speculation``: a speculation on the cause/consequences of an event that happened in reality
    * ``willingness``: a willingness prompting action
    * ``opportunity``: opportunity to decrease the work required to accomplish a task
    * ``unknown``: any other categorie

    These items should be made available in the network from the start. All new items should fit into one of these categories. Otherwise, it should be possible to add a new primary node.

.. image:: ../../../../static/img/BS5.png
    :width: 400
    :alt: Behaviour 5: SPEC

TEST SPEC

    All these nodes need to be available in the network from the start:

    * ``creativity``
    * ``passion``
    * ``performance``
    * ``power``
    * ``physical-stimuli``
    * ``memory``
    * ``imagination``
    * ``emotion``
    * ``thought``
    * ``speculation``
    * ``willingness``
    * ``opportunity``
    * ``unknown``

.. _prioritize_tasks_behaviour:

Prioritize tasks
----------------

BS6
~~~

SPEC

    Each node should have the following properties:

    * ``due-date``: the date the task is due to be completed
    * ``priority``: a value that should help with prioritization. It is to be discussed what this value varies in function of. *E.g.*: In the working context, it varies based on the customer needs, meaning the customer decides the prioritization.

.. image:: ../../../../static/img/BS6.png
    :width: 400
    :alt: Behaviour 6: SPEC

TEST SPEC

    * ``due-date``: the due date should be persisted
    * ``due-date``: the due date should be editable
    * ``priority``: the priority should be persisted
    * ``priority``: the priority should be editable

.. _track_task_progress_behaviour:

Track progress of tasks
-----------------------

BS7
~~~

SPEC

    Each node should have the following properties:

    * ``focus-toggle``: a toggle to indicate whether the task is being engaged with or not. A task can be engaged with either from ``analysis`` or from what the task requires to be completed.

    Only one task can be engaged with at a time. The previous engaged task becomes unengaged if a new one is engaged with.

    A time counter initiates when a task is engaged with and it stops when the task is not engaged with. There's an accumulator variable holding the total time of focus time.
    * ``focus-type``: the type of focus the task is being engaged with. It can be either ``analysis`` or ``execution``. ``analysis`` means the task is being analyzed before being executed. It can be interesting to understand how much time goes into understanding a problem and how much goes into solving it.

.. image:: ../../../../static/img/BS7.png
    :width: 400
    :alt: Behaviour 7: SPEC

TEST SPEC

    Each node should have the following properties:

    * verify that the ``focus-type==analysis`` saves the time spent in the accumulator variable ``focus_type_analysis``
    * verify that the ``focus-type==execution`` saves the time spent in the accumulator variable ``focus_type_execution``
    * verify that the ``focus-toggle`` stops and restarts the counter.
    * verify that the ``focus-toggle`` the accumulator persists the total time of focus time.
    * verify that the ``focus-toggle`` stops the focus toggle on a different task and that that different task focus time accumulator is duly updated.

BS8
~~~

SPEC

    All tasks are actionable tasks because all tasks can at least be ``analysed``. It may be interesting to know:
    * ``number-of-subtasks``: the total number of child tasks
    * ``number-of-leaves``: the total number of child tasks that are leaves

.. image:: ../../../../static/img/BS8.png
    :width: 400
    :alt: Behaviour 8: SPEC

TEST SPEC

    Each node should have the following properties:

    * verify that the ``number-of-subtasks`` is correct
    * verify that the ``number-of-subtasks`` is correct after a task is removed
    * verify that the ``number-of-leaves`` is correct
    * verify that the ``number-of-leaves`` is correct after a task is removed

BS9
~~~

SPEC

    The ``total-time-spent-on-subtasks`` provides a metric that can help understanding **how much work has been put into this task**. It is still uncertain how this help understanding the progress of the task, but it is a good start. The ``total-time-spent-on-subtasks`` refers either to:

    * the task itself;
    * or to the total sum of the tree taking the task as root;
    * or to the total sum of the leaves of the tree taking the task as root;

    * ``total-time-spent-on-task==analysis``: the total time spent on the task analyzing
    * ``total-time-spent-on-task==execution``: the total time spent on the task executing
    * ``total-time-spent-on-task``: the total time spent on the task
    * ``total-time-spent-on-subtasks==analysis``: the total time spent on all tasks analyzing
    * ``total-time-spent-on-subtasks==execution``: the total time spent on all tasks executing
    * ``total-time-spent-on-subtasks``: the total time spent on all tasks
    * ``total-time-spent-on-leaves==analysis``: the total time spent on all leaves analyzing
    * ``total-time-spent-on-leaves==execution``: the total time spent on all leaves executing
    * ``total-time-spent-on-leaves``: the total time spent on all leaves

.. image:: ../../../../static/img/BS9.png
    :width: 400
    :alt: Behaviour 9: SPEC

TEST SPEC

    Each node should have the following properties:

    * verify that ``total-time-spent-on-task==analysis`` is correct
    * verify that ``total-time-spent-on-task==execution`` is correct
    * verify that ``total-time-spent-on-task`` is correct
    * verify that ``total-time-spent-on-subtasks==analysis`` is correct
    * verify that ``total-time-spent-on-subtasks==execution`` is correct
    * verify that ``total-time-spent-on-subtasks`` is correct
    * verify that ``total-time-spent-on-leaves==analysis`` is correct
    * verify that ``total-time-spent-on-leaves==execution`` is correct
    * verify that ``total-time-spent-on-leaves`` is correct
    * verify that ``total-time-spent-on-subtasks==analysis`` is updated after removing any subtask
    * verify that ``total-time-spent-on-subtasks==execution`` is updated after removing any subtask
    * verify that ``total-time-spent-on-subtasks`` is updated after removing any subtask
    * verify that ``total-time-spent-on-leaves==analysis`` is updated after removing any leave
    * verify that ``total-time-spent-on-leaves==execution`` is updated after removing any leave
    * verify that ``total-time-spent-on-leaves`` is updated after removing any leave


