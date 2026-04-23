| dt4acc
| ======

| Pattern-based toolkit for digital twins of synchrotron light sources.

| Overview
| --------

| **dt4acc** provides the required infrastructure to build digital twins for particle accelerators.
| It delivers most of the implementation (~90%), so new twins mainly require adapting the control system interface.

| A dt4acc digital twin is primarily a **virtual accelerator (test bench)** used to develop and test control software before the real machine is available.

| Repositories
| ------------

| To build a twin, use **both repositories**:

| - https://github.com/dt4acc/dt4acc  
|   Runnable framework for building a digital twin

| - https://github.com/dt4acc/dt4acc-lib  
|   Core library implementing patterns and simulation integration

| Relationship:

| - ``dt4acc-lib`` = core infrastructure and patterns  
| - ``dt4acc`` = runnable twin built on top  

| Key Concepts
| ------------

| - Pattern-based architecture (see papers below)
| - Interaction model:

|   - **ReadCommands** → read state  
|   - **Commands** → change state  

| - Translator service connects simulation and control system

| Control Systems
| ---------------

| - Supported: **EPICS**, **TANGO**  
| - Planned: **DOOCS**

| Getting Started (minimal)
| -------------------------

| .. code-block:: bash

|    python3 -m venv venv
|    source venv/bin/activate

|    pip install git+https://github.com/dt4acc/dt4acc-lib
|    pip install git+https://github.com/dt4acc/dt4acc

| Requires Python 3.10+

| More Information
| ----------------

| For full documentation, architecture details, and references:

| - README_details.rst

| **Important:**  
| The file ``README_details.rst`` contains the complete description of:

| - architecture and building blocks  
| - digital twin concepts  
| - scientific references  
| - usage guidance  

| It is intended to be read **together with this file**.

| License
| -------

| GPL v3
