.. raw:: html

   <a href="https://github.com/lifespline/backlog.git"><img loading="lazy" width="149" height="149" src="https://github.blog/wp-content/uploads/2008/12/forkme_left_darkblue_121621.png?resize=149%2C149" class="attachment-full size-full" alt="Fork me on GitHub" data-recalc-dims="1"></a>

=====================
TR2.1: Rendering Host
=====================

About
-----

The library rendering the network requires a host.

Solution
--------

The network rendering host is a jupyter notebook.

Definition of ready
-------------------

* Validating POC: `Rendering a graph network on a local jupyter notebook <https://lifespline.github.io/samples-networkx/src/samples_docs.html>`_

Acceptance Criteria
-------------------

* add task runner task to setup up the jupyter server
* have a jupyter notebook that displays the network according to a template
* render a graph network from a database in a jupyter notebook

QA Acceptance Criteria
----------------------

* documentation
* PR documentation

Pull Request
------------

`CODE <https://github.com/lifespline/backlog/pull/CODE>`_

Requirements Dependencies
-------------------------

* ``TR2.1: Rendering Host``
    * ``TR2.2: Network persistence interface``
