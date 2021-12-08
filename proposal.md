# Community Software Analysis Proposal
Please edit this file and push to your repository.

## Software: [SU2](https://su2code.github.io/)

*Write a paragraph describing what the software does and who its
primary audience is.*

>[SU2](https://github.com/su2code/SU2) is a multiphysics / CFD tool written in C++. Mostly used in fluid dynamics and aerodynamics applications, SU2 is expanding into reactive flow (with integration into packages like [Cantera](https://cantera.org/)). Specifically, SU2 solves compressible and incompressible Navier Stokes equations,  compressible and incompressible Euler, and applies both a Shear Stress Transport (SST) model and a Spalar-Allmaras (S-A) model for turbulence modeling (turbulence modeling employs the Finite Volume Method). SU2 can extend into structural analysis with elasticity modeling (FEM). SU2 can also calculate heat conduction using FVM to discretize in space. SU2 seems geared toward aerospace and fluid mechanics applications as used by both industry/production users (e.g., Boeing, Bosch, Airbus) and academic users. 

### Stats

| Description | Your answer |
|---------|-----------|
| Repository URL |  https://github.com/su2code/SU2  |
| Main/documentation website | [Main](https://su2code.github.io/) + [Documentation](https://su2code.github.io/docs_v7/home/)  |
| Year project was started | 2013  |
| Number of contributors in the past year | 3118 |
| Number of contributors in the lifetime of the project | 14,827 |
| Number of distinct affiliations | 6-10 (Stanford, Bosch, Airbus, University of Twente, etc.) |
| Where do development discussions take place? | [Slack](https://join.slack.com/t/su2devteam/shared_invite/zt-af0uuqf8-8XNExKMV9G~UVsnkvi5uVA), [CFD Online](https://www.cfd-online.com/Forums/su2/), and GitHub [Issues/Discussions](https://github.com/su2code/SU2/discussions)|
| Typical number of emails/comments per week? | ~10-20 |
| Typical number of commits per week? | ~30 (min 8, max 95)  |
| Typical commit size | ~100 - 200 lines inserted (max 1294, min 1)|
| How does the project accept contributions? | [Guidelines](https://su2code.github.io/develop.html) -> Log issues and feature requests through GitHub issue tracker, fork SU2, push changes, submit pull request|
| Does the project have an automated test suite? | yes |
| Does the project use continuous integration? | yes|
| Are any legal/licensing steps required to contribute? | no / [LGPL 2.1 License](https://github.com/su2code/SU2/blob/master/LICENSE.md) |

### Install and run

Check the following boxes when complete or add a note below if you
encountered a problem.

- [X] I have installed the software
- [X] I have run at least one example
- [X] I have run the test suite
- [X] The test suite passes

### Notes/concerns/risks

Please comment on any anomalies or known risks to following this
project, if you were unable to answer any questions above, or
otherwise have concerns about the appropriateness of the software.  If
the project requires a contributor license agreement or other
procedural steps, please explain here.  "None at this time" is
acceptable for this question.

> This community is not as vocal on Slack as some of the other packages I looked at (e.g., [Devito](https://github.com/devitocodes/devito)). I am slightly concerned about response times with this community though they have been responsive to students in the past. For the actual pull request part of this assignment, I may choose to look at a few tools (e.g. LibCEED, Devito, etc.) in comparison to SU2 but for the community analysis aspect I will focus on SU2. 

#### Note on copyright
Students retain copyright on any work done in completion of a CU
course, so you are authorized to sign a [contributor license
agreement (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement),
affirm a [developer's certificate of
origin (DCO)](https://en.wikipedia.org/wiki/Developer_Certificate_of_Origin),
etc.  If you have concerns about this, please note them and/or reach
out to Jed directly.

---
### Community Engagement
I created a discussion [here](https://github.com/su2code/SU2/discussions/1441#discussion-3686823) and posted to the SU2 slack [here](https://su2devteam.slack.com/archives/C2A1JLGDR/p1636657760008000).


---
### Contribution

#### Proposed Changes
- The idea here is to see how SU2's different time stepping schemes converge at different time step sizes in unsteady simulations. While I am not entirely sure that I have accomplished this goal, I think this takes a step toward understanding of how SU2's time integrators vary with different time steps. 
- I have added `time_convergence.py`, a Python script based on `computer_order_of_accuracy.py` [here](https://github.com/su2code/VandV/blob/ad27cdf9391c9077f3ef14949e29c01be428b0d9/mms/fvm_navierstokes/compute_order_of_accuracy.py). This script loops over various different time marching schemes (e.g., `TIME_MARCHING = TIME_STEPPING`, `TIME_MARCHING = DUAL-TIME_STEPPING-1ST_ORDER`, `TIME_MARCHING = DUAL-TIME_STEPPING-2ND_ORDER`) for each of SU2's Navier Stokes Solvers (e.g., `FEM_NAVIER_STOKES` and `NAVIER_STOKES`) using different numerical methods (e.g., DG, JST, ROE+LIM, ROE, ROW+WLS).  Each case is evaluated at a different `TIME_STEP` size [1e-6 : 1e-10]. 
- Since no MMS cases for unsteady Navier Stokes exist in SU2, I merely plotted the mean of rms[Rho],  rms[RhoU],  rms[RhoV], and rms[RhoE] for each of the above cases. 
- Some parameters: 
	- Mesh: currently uses a quad mesh generated by `create_grid_quad.py` copied over from the `fvm_navier_stokes` VandV example.
	- TIME_ITER : 15
	- Time Discretization: employs the default for each Numerical method (e.g., RUNGE-KUTTA_EXPLICIT for DG and EULER_IMPLICIT for FVM)
	- Fluid properties are uniform across the 4 configuration files: 
		- lam_mms_dg_unst.cfg : FEM unsteady Navier Stokes Flow on Unit Quad using Discontinuous Galerkin
		- lam_mms_jst_unst.cfg : FVM unsteady Navier Stokes Flow on Unit Quad using JST
		- lam_mms_roe_lim_unst.cfg : FVM unsteady Navier Stokes Flow on Unit Quad using ROE + LIM
		- lam_mms_roe_unst.cfg : FVM unsteady Navier Stokes Flow on Unit Quad using ROE 
		- lam_mms_roe_wls.unst.cfg : FVM unsteady Navier Stokes Flow on Unit Quad using WLS
	 
#### Related Work
- The structure for this work was based off of the `fvm_navier_stokes` and `dg_navierstokes` VandV examples.
- To automate updating of the `.cfg` in `update_ts.py`, I employed a script found here: [Edit configuration file through python - Stack Overflow](https://stackoverflow.com/a/5305696)
