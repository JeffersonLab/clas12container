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
 docker run -it --rm  -v ~/mywork:/jlab/work/mywork jeffersonlab/clas12simulations:iprod bash
 cd mywork
 clasdis --trig 1000 --docker --t 25 35
 gemc -USE_GUI=0 -N=100 -INPUT_GEN_FILE="lund, sidis.dat" /jlab/clas12Tags/gcards/rga-spring2018.gcard
 evio2hipo -r 11 -t -1.0 -s -1.0 -i out.ev -o gemc.hipo
 createClaraCook.csh gemc.hipo rga-spring2018 1
 clara-shell cook.clara

Notice: if you have multiple cores, specify them as the last argument for createClaraCook.csh. For example, if you have 4 cores::

 createClaraCook.csh gemc.hipo rga-spring2018 4

You can find the number of cores of your system by issuing this command::

 sysctl hw.physicalcpu hw.logicalcpu


|br|



Quickstart: GEMC examples, interactively (MacOS)
================================================

Use the following commands (on Mac) to run gemc interactively::

 defaults write org.macosforge.xquartz.X11 enable_iglx -bool true
 xhost +127.0.0.1
 docker run -it --rm -e DISPLAY=docker.for.mac.localhost:0 jeffersonlab/clas12simulations:iprod bash
 cd /jlab/clas12Tags/4.3.1/experiments/clas12/ctof/
 gemc ctof.gcard



|br|




Quickstart: Submit Jobs to OSG
==============================

Work in progress, coming soon.



|br|



Container content
=================

The clas12simulations docker image contains:

- various :ref:`generators <generators>` 
- gemc with the clas12 geometry
- CLARA
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



