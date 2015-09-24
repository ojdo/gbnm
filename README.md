# Globalized Nelder-Mead method

This repository contains the MATLAB/Octave function `gbnm` that implements the algorithm described in this paper:

Luersen, Marco A., and Rodolphe Le Riche. "[Globalized Nelder–Mead method for engineering optimization](http://www.emse.fr/~leriche/gbnm_cas.pdf)." Computers & structures 82.23 (2004): 2251-2260.

As the title implies, it is a classical [Nelder-Mead method](https://en.wikipedia.org/wiki/Nelder%E2%80%93Mead_method) with some extras for dealing with multiple local optima. The function itself has the following signature:

## Usage

    [x, fval, output, options] = gbnm(fun,xmin,xmax[, options])
    
### Arguments

    fun        A handle of the function to be minimized
    xmin       Column vector of lower bounds
    xmax       Column vector of upper bounds
    options    (optional) Structure with optimization algorithm parameters

### Return values

    x          The found global minimum
    fval       Function value at the found best minimum
    output     Structure with all found local minima and initial simplices
    options    Structure of parameters which were used during optimization
    
### Options

    options.maxRestarts = 15; % maximum (probablistic or degenerated) restarts
    options.maxEvals = 2500;  % maximum function evaluations
    options.nPoints = 5;      % number of random points per restart
    
    options.maxIter=250;      % maximum iterations per restart
    options.alpha = 1;        % reflection coeff
    options.beta = 0.5;       % contraction coeff
    options.gamma = 2;        % expansion coeff
    options.epsilon = 1e-9;   % T2 convergence test coefficient
    options.ssigma = 5e-4;    % small simplex convergence test coefficient
    
More details on the options and the can be found in the paper linked above.

## Practical considerations

This might become an FAQ section, if any Q's will being asked.

From my experience, the number of parameters (`length(xmin)`) should be small, e.g. up to 5 or 6.

As -- depending on the number of parameters -- several thousand iterations (i.e. evaluations of function `fun`) are needed, its runtime should be as short as possible (as in fractions of a second).

## Copyright

Copyright (C) 2015  Johannes Dorfner

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>
