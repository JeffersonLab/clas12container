.. clas12softwarePage documentation master file, created by
   sphinx-quickstart on Thu Jul 26 10:01:44 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. |br| raw:: html

   <br>

|br|

The CLAS12 software packages are distributed using docker images.


Quickstart: Full chain using docker
===================================

Use the following command to run the clas12 software image using a "~/mywork" local directory, and run clasdis events through the GEMC/COATJAVA chain::

 mkdir -p ~/mywork
 docker run -it --rm  -v ~/mywork:/jlab/work/mywork jeffersonlab/clas12software:production bash
 cd mywork
 clasdis --trig 1000 --docker --t 25 35
 gemc -USE_GUI=0 -N=100 -INPUT_GEN_FILE="lund, sidis.dat" /jlab/clas12Tags/gcards/rga-spring2018.gcard
 evio2hipo -r 11 -t -1.0 -s -1.0 -i out.ev -o gemc.hipo


|br|



Quickstart: GEMC examples, interactively (MacOS)
================================================

First, open the XQuartz app and go to preferences and activate the option ‘Allow connections from network clients’ in XQuartz settings.
This will allow XQuartz to receive display messages from network clients, such as docker.

Second, from any terminal::

    defaults write org.macosforge.xquartz.X11 enable_iglx -bool true

This will be useful when running gemc: it will allow OPENGL to use your graphic card.

|br|

Restart XQuartz to activate these changes.

|br|

Finally, add your localhost to the list of accepted X11 connections::

 xhost +127.0.0.1

You should be able now to run docker and use the native X server to open windows application. For example::

 docker run -it --rm -v ~/mywork:/jlab/work/mywork -e DISPLAY=docker.for.mac.localhost:0 jeffersonlab/clas12software:production bash

|br|


Quickstart: GEMC examples, interactively (Linux)
================================================

Add your localhost to the list of accepted X11 connections with one of these two commands (if the first doesn't work, try the second one):

.. code-block:: ruby

 xhost 127.0.0.1
 xhost local:root

Export the env variable DISPLAY:

.. code-block:: ruby

 export DISPLAY=:0

Run the command using your local x11 tmp dir:

.. code-block:: ruby

 docker run -it --rm -v /tmp/.X11-unix:/tmp/.X11-unix -v ~/mywork:/jlab/work/mywork -e DISPLAY=$DISPLAY  jeffersonlab/clas12software:production /bin/bash

|br|



|br|




Quickstart: Submit Jobs to OSG
==============================

Work in progress, coming soon.



|br|



Container content
=================

The clas12software:production docker image contains:

- various :ref:`generators <generators>` 
- gemc with the clas12 geometry
- Coatjava
- the *CLAS12_BIN*, *CLAS12_LIB*, *CLAS12_INC* dirs and environment variables


For the packages version check the :ref:`tags <tags>` page.


|br|


HowTos
======

.. toctree::
	:maxdepth: 1

	examples


Tags
====

.. toctree::
	:maxdepth: 1

	tags




Troubleshooting
---------------

- `Linux: Solving Docker permission denied while trying to connect to the Docker daemon socket <https://techoverflow.net/2017/03/01/solving-docker-permission-denied-while-trying-to-connect-to-the-docker-daemon-socket/>`_

|



