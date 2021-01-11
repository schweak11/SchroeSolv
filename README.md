# SchroeSolv
Numerical solver of the Schroedinger Equation in 1D

Description:
This program can find the energy eigenvalues and eigenfunctions Psi for the 1D Schrödinger equation or the 3D Radial Schrödinger equation with Psi = R(r)*r (the radial wavefunction R(r) is given by dividing the output Psi by r). The wavefunction is written to a file, and the eigenenergy is displayed in the terminal.

How to use:
The potential is entered as function V(x) in line 43, the program is set up with the finite square well potential. The mass m and, for the radial case, the angular momentum l are entered as variables.

Numerical parameters:
dx is the stepsize used for the Runge-Kutta method, Ψ(xfinal) tol is the allowed deviation of the computed wave function from Ψ(xfinal) and MaxNoIt the maximum number of iterations in the root-finding bisection procedure. EminStart and EmaxStart are the limits of the energy interval in which the root is searched.

Numerical tips
Boundary conditions:
The boundary conditions are entered in lines 24-28.
For odd states in 1D, Ψ1(xinitial) = 0 and Ψ1'(xinitial) = 1
For even states in 1D, Ψ1(xinitial) = 1 and Ψ1'(xinitial) = 0
For the radial case, Ψ1(xinitial) = 0 and Ψ1'(xinitial) = 1
For the radial case, make xinitial = 0.001 to avoid division by zero.
Technically, any nonzero value would be allowed instead of the 1s due to later normalization, but then Ψ(xfinal) tol has to be adjusted to stop the root-finding process accordingly. This problem vanishes as the last interval becomes large compared to the others, so Ψ1(xfinal) = 0 is approached exponentially and not "cut-off-like" as in the infinite well.

Known caveats:
The bisection algorithm finds a solution within the given energy limits, make sure to try different lowerE and upperE.
Often, a potential has no bound state. This can be seen by the energy approaching one of the limits. Look at the end of the wavefunction and see if it approaches 0. If yes, try making the potential deeper.
Often, when the iterations reach the true energy, the solution is fine for low x but diverges for larger x. This is the typical behaviour of the method, as E approaches the true value, the point of divergence moves to infinity.

Negative/positive potentials:
For potentials that do not go to zero at infinity (infinite well, SHO), the potential is positive, as well as the stationary state energies. For potentials that go to zero at infinity (finite well, Coulomb, Exp), the convention is to make the potential as well as the stationary state energies zero.

