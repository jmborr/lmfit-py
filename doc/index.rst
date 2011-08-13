.. lmfit documentation master file,

Non-Linear Least-Square Minimization for Python
================================================

.. _scipy.optimize.leastsq: http://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.leastsq.html
.. _scipy.optimize.l_bfgs_b: http://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.fmin_l_bfgs_b.html
.. _scipy.optimize.anneal: http://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.anneal.html

.. _Levenberg-Marquardt: http://en.wikipedia.org/wiki/Levenberg-Marquardt_algorithm
.. _L-BFGS:  http://en.wikipedia.org/wiki/Limited-memory_BFGS
.. _simulated annealing: http://en.wikipedia.org/wiki/Simulated_annealing

.. _MINPACK-1: http://en.wikipedia.org/wiki/MINPACK

The lmfit Python package provides a simple, flexible interface to non-linear least-squares
optimization, or curve fitting.  By default, LMFIT uses the `Levenberg-Marquardt`_
minimization algorithm from `MINPACK-1`_ as implemented in `scipy.optimize.leastsq`_, but
it can also use the `L-BFGS`_ (limited memory Broyden-Fletcher-Goldfarb-Shanno) algorithm
as implemented in `scipy.optimize.l_bfgs_b`_ or the `simulated annealing`_ algorithm as
implemented in `scipy.optimize.anneal`_.  Support for other optimization routines may be
added in the future.  While these functions from scipy.optimize provide the core numerical
algorithm for non-linear least-squares minimization, the lmfit package adds a few simple
conveniences.  Most of this document will assume that the Levenberg-Marquardt algorithm is
being discussed, as it appears to be the most robust for finding local minima of
well-described models of scientific measurements.

For any minimization problem, the programmer must provide a function that takes a set of
values for the variables in the fit, and produces the residual function to be minimized in
the least-squares sense.

The lmfit package allows models to be written in terms of a set of Parameters, which are
extensions of simple numerical variables with the following properties:

 * Parameters can be fixed or floated in the fit.
 * Parameters can be bounded with a minimum and/or maximum value.
 * Parameters can be written as simple mathematical expressions of
   other Parameters.  These values will be re-evaluated at each
   step in the fit, so that the expression is statisfied.  This gives
   a simple but flexible approach to constraining fit variables.

The main advantage to using Parameters instead of fit variables is that the model function
does not have to be rewritten for a change in what is varied or what constraints are
placed on the fit.  The programmer can write a fairly general model, and allow a user of
the model to change what is varied and what constraints are placed on the model.

In addition, lmfit calculates are reports the estimated uncertainties
and correlation between fitted variables.

.. toctree::
   :maxdepth: 2

   installation
   parameters
   fitting
   constraints
