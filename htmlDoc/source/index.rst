.. clas12softwarePage documentation master file, created by
   sphinx-quickstart on Thu Jul 26 10:01:44 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. |br| raw:: html

   <br>

|br|

The CLAS12 software packages are distributed using docker images.


Quickstart: Docker
==================

Use the following command to run the clas12 software image using a "~/mywork" local directory, and run clasdis events through the GEMC/COATJAVA chain::

 mkdir -p ~/mywork
 docker run -it --rm  -v ~/mywork:/jlab/work/mywork jeffersonlab/clas12simulations:iprod bash
 clasdis --trig 1000 --docker --t 25 35
 gemc -USE_GUI=0 -N=100 -INPUT_GEN_FILE="lund, sidis.dat"  /jlab/clas12Tags/gcards/clas12-default.gcard 


|br|


Quickstart: Submit Jobs to OSG
==============================

Work in progress, coming soon.

..
   Login to scosg16 and copy the steering card template somewhere you can edit::

   ssh scosg16.jlab.org
   cp /group/clas12/offsite-simulations/scard.txt .
   EDIT FILE

   Run submit.py with -s option to submit jobs to OSG::

   /group/clas12/offsite-simulations/submit.py -s scard.txt


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



