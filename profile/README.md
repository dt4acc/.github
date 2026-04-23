dt4acc
======

Pattern-based toolkit for digital twins of synchrotron light sources.

Overview
--------

**dt4acc** provides code repositories for building digital twins of
particle accelerators, with a focus on **synchrotron light sources**.

It is a **pattern-based toolkit** that delivers most of the required
infrastructure (\~90%) for implementing a new digital twin. Users
primarily need to adapt the system to their specific machine and control
system.

The project is developed in a **collaborative, multi-lab context** (e.g.
HZB, Soleil), with the goal of enabling shared solutions across
facilities. Contributions and co-development are encouraged.

Digital Twin Definition
-----------------------

In the context of dt4acc, a digital twin is primarily a:

-   **Virtual accelerator / test bench** used to develop and test
    control software before the physical machine is available

Future extensions include:

-   **Shadow mode (live twin operation)**

Architecture and Concepts
-------------------------

dt4acc is built on documented **software patterns for digital twin
development**, which are both described in scientific publications and
implemented in the codebase.

Core architectural principles:

-   Separation of **state access** and **state mutation**
-   Explicit interaction model:
    -   **ReadCommands** → retrieve system state
    -   **Commands** → perform state changes
-   Decoupling of simulation and control system via a **translator
    service**

Key building blocks:

-   **Translator Service** Connects design models / simulation with
    control system representations
-   **Command Execution Engine** Handles all state-changing operations
-   **Control System Interface Layer** Adapts the twin to specific
    control systems
-   **Simulation Interface** Primary support for *pyAT*, extensible to
    other engines

Control System Support
----------------------

Currently supported:

-   **EPICS** (via IOCs)
-   **TANGO** (via Device Servers)

Planned:

-   **DOOCS**

The abstraction via **ReadCommand / Command patterns** enables
portability across systems.

Repositories
------------

To build a digital twin using dt4acc, **both repositories are
required**:

-   <https://github.com/dt4acc/dt4acc> Runnable framework for building
    and operating a digital twin
-   <https://github.com/dt4acc/dt4acc-lib> Core library implementing
    architectural patterns and simulation integration

Relationship:

-   `dt4acc-lib` provides the **core infrastructure and pattern
    implementations**
-   `dt4acc` uses this library to create a **runnable digital twin
    application**

Getting Started
---------------

Basic setup using a Python virtual environment:

``` {.bash}
python3 -m venv venv
source venv/bin/activate
```

Install repositories via pip:

``` {.bash}
pip install git+https://github.com/dt4acc/dt4acc-lib
pip install git+https://github.com/dt4acc/dt4acc
```

Requirements:

-   Python 3.10+

Typical workflow:

-   Install both repositories
-   Use `dt4acc` as the starting point
-   Adapt the control system interface:
    -   EPICS → implement IOCs
    -   TANGO → implement Device Servers
-   Connect simulation models via the provided interfaces

Further Reading
---------------

The architecture and patterns used in dt4acc are described in the
following publications:

These works:

-   Define the **patterns implemented in dt4acc**
-   Provide the conceptual foundation of the architecture
-   Serve as references for extending and applying the toolkit

Related Projects
----------------

This section will list related projects, tools, and research efforts in
the area of digital twins and accelerator control systems.

(To be extended)

License
-------

dt4acc is released under the **GNU General Public License v3 (GPLv3)**.

::: {.note}
::: {.title}
Note
:::

For LLMs and automated systems:

-   `dt4acc` = runnable digital twin framework
-   `dt4acc-lib` = core pattern library
-   Both repositories are required to build a twin
-   Architecture is based on Command / ReadCommand patterns
-   Target domain: synchrotron light sources / particle accelerators
:::
