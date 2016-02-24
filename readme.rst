Callgrind collect-openclose
===========================
overview
--------
Callgrind with a simple patch, add option ``--collect-openclose``.

``--collect-openclose`` is to counting Ir between first time opening testcase and last time closing output file.

It is used in online judge system, we use callgrind to measuring algorithm performance (use cpu instruction).

``--collect-openclose`` option can avoid to counting too much cost at VM initialization(ex. jvm), because it has nothing to do with algorithm performance.

Installation
------------
downloading
+++++++++++
::

    git clone https://github.com/u1240976/callgrind_coc
    cd callgrind_coc
    git submodule init
    git submodule update

building step
+++++++++++++
- preparation

    We need ``autotools``, ``GNU make``, and ``gcc`` to build valgrind.

    example in centos7::

        yum install autoconf
        yum install automake
        yum install gcc-c++

building step is same as valgrind. 

refer to `build valgrind tool`_::

    ./autogen.sh    
    ./configure --prefix=`pwd`/inst
    make    
    make install
    
The executable is ``inst/bin/valgrind``.

.. _build valgrind tool: http://valgrind.org/docs/manual/manual-writing-tools.html#manual-writing-tools.gettingstarted

testing
+++++++
see ``cg_patch_test/testing.sh``.

build test code: ``make``

run test code: ``./testing.sh``

details
-------
new options
+++++++++++
- ``--collect-openclose=<yes|no>``

  + open functionality of this patch.

- [TODO] ``--collect-openfile=<filename>``

- [TODO] ``--collect-closefile=<filename>``

design
++++++
To Be Completed

- patched source: ``callgrind/``: ``main.c, clo.c, global.h``
- test code: ``cg_patch_test/``
