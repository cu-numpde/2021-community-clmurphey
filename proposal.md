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
| Main/documentation website | [Main](https://su2code.github.io/) + [Documentation](https://su2code.github.io/docs_v7/home/) ) |
| Year project was started | 2013  |
| Number of contributors in the past year | |
| Number of contributors in the lifetime of the project | 14,827 |
| Number of distinct affiliations | 6-10 (Stanford, Bosch, Airbus, University of Twente, etc.) |
| Where do development discussions take place? | [Slack](https://join.slack.com/t/su2devteam/shared_invite/zt-af0uuqf8-8XNExKMV9G~UVsnkvi5uVA)  |
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
