*************************************************************
## MaMuPaXS
 - Version 1.0, July, 2023
 - Author(s):  Rafael L. Delgado
 - Email:  rafael.delgado@upm.es
*************************************************************

 DESCRIPTION
-------------------------------------------------------------
Evaluating total cross sections from differential cross sections
for 2->n processes, with n>2, can be challenging. This code is
intented for solving such problem for massless initial and
final state particles and n=3,4 and 5. In 

Part of the code is Fortran code that compiles to a Python module
via F2PY. For the multidimensional numerical integration, the
VEGAS algorithm is used via the class vegas.Integrator from the
vegas Python module (G.P.Lepage, J.Comput.Phys.**27** (1978) 192
and J.Comput.Phys.**439** (2021) 110386).

 REQUIREMENTS
-------------------------------------------------------------
This code requires a working Fortran compiler and a Python 3
installation. The Python packages vegas, Numpy and F2PY should
be available. Optionally, MPI can be used for parallelizing
the Monte Carlo integration. For using this option, the mpi4py
Python module is also required.

 COMPILING
-------------------------------------------------------------
The repository includes a Makefile. The only required command
is:

```make```

 USAGE
-------------------------------------------------------------
We have include the Python script *phase_space.py^* that computes
the phase space for the 2->n processes with n=2,3,4 and 5. This is
intended to be a test of the code as well as an usage example.

The compilation process generates a Python 3 module on the compiling
directory. Such a module should be loaded into Python via the instruction

```
    from amp import amp
```

Afterwards, the instructions
```
    amp.only_phase_space=True
    amp.v=0.256
    amp.s=1.e-0
```
load v=256MeV, s=1TeV on the evaluation routines. The variable
```only_phase_space``` is set to ```True``` only for evaluating
the phase space. If you are to compute a total cross secction,
```amp.only_phase_space=False``` should be used instead.

The matrix elements are coded inside the files

* **M_2to2.h**, for a 2->2 process
* **M_2to3.h**, for a 2->3 process
* **M_2to4.h**, for a 2->4 process
* **M_2to5.h**, for a 2->5 process

In each of these files, the code should return a value with
the matrix element on the ```M``` variable. The following variables
can be used (notation: i,j=1,2,3,4,5):

* **fi**      :
* **zi**      :
* **zij**     :
* **th_c(i)** :
* **th_s(i)** :
* **phi(i)**  :

 LICENSE
-------------------------------------------------------------

GNU General Public License (GPLv3).
See detailed text in the [LICENSE](./LICENSE.md) file.

 ATTRIBUTION
-------------------------------------------------------------
