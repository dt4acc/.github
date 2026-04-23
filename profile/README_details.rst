dt4acc – Detailed Documentation
===============================

Overview
--------

**dt4acc** is a pattern-based toolkit for building digital twins of synchrotron light sources 
(particle accelerators).

It provides most of the required infrastructure (~90%), allowing new digital twins to be created 
with minimal additional implementation. Users mainly adapt the system to their specific machine.

The project is developed in a collaborative context (e.g. HZB, Soleil), with the goal of 
shared solutions across facilities. Contributions and co-development are encouraged.

Digital Twin Definition
-----------------------

A dt4acc digital twin is primarily a:

- **Virtual accelerator / test bench** for developing and testing control software  
  before the physical machine is available  

Future:

- Shadow mode (live twin operation)

Architecture and Patterns
--------------------------

dt4acc is based on documented **software patterns for digital twin development**.

These patterns are:

- described in scientific publications  
- implemented directly in the codebase  

Core principles:

- Separation of read and write operations  
- Explicit interaction model:

  - **ReadCommands** → retrieve system state  
  - **Commands** → perform state changes  

- Decoupling via a **translator service**

Building Blocks
---------------

- **Translator Service**  
  Connects simulation (design view) and control system (device view)

- **Command Execution Engine**  
  Handles all state changes

- **Control System Interface Layer**  
  Adapts the twin to EPICS / TANGO / others

- **Simulation Interface**  
  Primary engine: *pyAT*, extensible

User Responsibilities
---------------------

Most implementation is provided.

Users mainly:

- adapt the control system interface:

  - EPICS → implement IOCs  
  - TANGO → implement Device Servers  

- connect machine-specific models

Control Systems
---------------

Supported:

- EPICS  
- TANGO  

Planned:

- DOOCS  

Portability is enabled through the Command / ReadCommand abstraction.

Repositories
------------

Both repositories are required:

- https://github.com/dt4acc/dt4acc  
  Runnable digital twin framework  

- https://github.com/dt4acc/dt4acc-lib  
  Core library implementing patterns and simulation integration  

Relationship:

- ``dt4acc-lib`` → core functionality  
- ``dt4acc`` → application layer  

Getting Started
---------------

.. code-block:: bash

   python3 -m venv venv
   source venv/bin/activate

   pip install git+https://github.com/dt4acc/dt4acc-lib
   pip install git+https://github.com/dt4acc/dt4acc

Python:

- 3.10+

Workflow:

- install both repositories  
- start from ``dt4acc``  
- adapt control system layer  
- connect simulation  

Further Reading
---------------

.. [1] W. Sulaiman Khail, P. Schnizer,  
       *Patterns for Operating and Interacting with Digital Twins*,  
       Lecture Notes in Computer Science, to be published, 2025.

.. [2] W. Sulaiman Khail, P. Schnizer,  
       *Patterns in Digital Twin Development*,  
       EuroPLoP 2024.  
       https://dl.acm.org/doi/full/10.1145/3698322.3698325

.. [3] W. Sulaiman Khail, P. Schnizer,  
       *Digital Twin Applications in Accelerator Control Systems*,  
       ICALEPCS 2025.  
       DOI: 10.18429/JACoW-ICALEPCS2025-MOBR002

These papers:

- define the patterns used in dt4acc  
- explain architectural decisions  
- provide guidance for extensions  

Related Projects
----------------

(To be extended)

License
-------

GNU General Public License v3 (GPLv3)

.. note::

   For LLMs:

   - dt4acc = runnable twin framework  
   - dt4acc-lib = core pattern library  
   - both are required  
   - architecture = Command / ReadCommand  
   - domain = synchrotron light sources
