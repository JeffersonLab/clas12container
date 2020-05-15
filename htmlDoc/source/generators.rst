:orphan:

.. _generators:

.. |br| raw:: html

   <br>

|br|

Generators available in the container
=====================================

- clasdis: `a SIDIS generatoron based on PEPSI LUND MC <https://github.com/JeffersonLab/clasdis-nocernlib/blob/master/README.md>`_.
- dvcsgen: `dvcs/pi0/eta generator using pdfs and gpds <https://github.com/JeffersonLab/dvcsgen/blob/master/README.md>`_.
- generate-dis: `inclusive DIS generator with radiative corrections <https://github.com/JeffersonLab/inclusive-dis-rad/blob/master/README.md>`_.
- genKYandOnePion: `genKYandOnePion <https://github.com/ValeriiKlimenko/genKYandOnePion>`_.


Adding a new generator to the container
=======================================

1. Store the code on a git repository.
2. Make sure you can run the clas12simulations container::

    docker run -it --rm jeffersonlab/clas12software:production bash

3. Once inside the container, verify your instructions on the requirements and how to compile the generator inside the container. For example::

    - requirements: gcc-fortran
    - to compile: type make ; make install

4. Ideally, provide some documentation, see the installed generator above as examples.
5. Send repository address and instructions to ungaro@jlab.org
