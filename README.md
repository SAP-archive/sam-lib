<!---
  SPDX-FileCopyrightText: 2023 SAP SE

  SPDX-License-Identifier: Apache-2.0
--->
![](https://img.shields.io/badge/STATUS-NOT%20CURRENTLY%20MAINTAINED-red.svg?longCache=true&style=flat) 

This public repository is read-only and no longer maintained.

[![REUSE status](https://api.reuse.software/badge/github.com/SAP/sam-lib)](https://api.reuse.software/info/github.com/SAP/sam-lib)

# The SAM Fortran library

## About this project

The SAM library is a collection of FORTRAN-77 subroutines for handling different
tasks in Finite Element Method solvers, such as the assembly of element matrices
into their global counterparts, solving global linear systems of equations,
solving eigenvalue problems, and some other lower-level matrix utilities, etc.

It was established by
[Kolbein Bell](https://app.cristin.no/results/show.jsf?id=328216) during the
1980s and 90s, and has been used in several FE program packages since then.

It is now made available under the
[Apache-2.0](https://spdx.org/licenses/Apache-2.0.html) license,
such that programs like FEDEM can still use it in their solvers.

## Requirements and Setup

The general compiler setup is performed using the cmake-configuration files of
the [cmake-modules](https://github.com/SAP/cmake-modules) repository,
which is consumed as a submodule by this repository.

The SAM library also uses a few [BLAS](https://www.netlib.org/blas/) subroutines,
and the dependency to that third-party module is handled by the `CMakeLists.txt`
files through the find-rules provided by the cmake installation.
On Linux, the BLAS library can be installed from the package manager,
e.g., on Ubuntu:

    sudo apt install libblas-dev

The SAM library can then be built and installed using, e.g.,

    mkdir Release; cd Release
    cmake .. -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=$HOME
    make install

This will build the two libraries in Release mode and install them
in the `$HOME/lib` folder.

Notice that by default the subroutines for the sparse matrix equation solver (in
the [src/SPR](src/SPR) folder) are compiled using 64-bit integer representation,
for handling of larger system matrices. This can be switched off by adding the
command-line option `-DBUILD_SPR_INTEGER8=OFF` to the cmake command above.
It will then use the standard 32-bit integer variables instead.

## Contributing

This project is open to feature requests, suggestions, bug reports, etc.,
via [GitHub issues](https://github.com/SAP/sam-lib/issues).
Contributions and feedback are encouraged and always welcome.
For more information about how to contribute,
see our [Contribution Guidelines](.github/CONTRIBUTING.md).

## Security / Disclosure

If you find any bug that may be a security problem, please follow our instructions at [in our security policy](https://github.com/SAP/sam-lib/security/policy) on how to report it. Please do not create GitHub issues for security-related doubts or problems.

## Code of Conduct

We as members, contributors, and leaders pledge to make participation in our community a harassment-free experience for everyone. By participating in this project, you agree to abide by its [Code of Conduct](https://github.com/SAP/.github/blob/main/CODE_OF_CONDUCT.md) at all times.

## Licensing

Copyright 2023 SAP SE or an SAP affiliate company and sam-lib contributors. Please see our [LICENSE](LICENSE) for copyright and license information. Detailed information including third-party components and their licensing/copyright information is available [via the REUSE tool](https://api.reuse.software/info/github.com/SAP/sam-lib).
