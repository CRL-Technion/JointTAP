# JointTAP

**C++ implementation of the Joint Task Assistance Planning (JointTAP) framework**
proposed in *Joint Task Assistance Planning via Nested Branch and Bound*, ICRA 2026.

This repository contains an implementation described in the accompanying paper of a nested branch-and-bound framework for solving the JointTAP problem, including an incremental optimal timing subsolver and a linear programming based upper bound.

---

## Repository Structure

```
.
├── joint_tap.h / joint_tap.cpp
├── lp_bound.h / lp_bound.cpp
├── incremental_otp.h / incremental_otp.cpp
├── assistance_otp.h / incremental_otp.cpp
├── utils.h / utils.cpp
├── tests/
└── ...
```

### Components

#### 1. JointTAP Solver

**Files:** `joint_tap.h`, `joint_tap.cpp`

Implements the nested Branch and Bound framework corresponding to **Algorithms 2 and 3** in the paper.

#### 2. Upper Bound Computation

**Files:** `lp_bound.h`, `lp_bound.cpp`

Implements the bounding technique described in **Section VI-A** of the paper.

#### 3. Incremental OTP Solver

**Files:** `incremental_otp.h`, `incremental_otp.cpp`

Implements the incremental optimal timing subproblem solver suggested in **Algorithm 1** in the paper. This solver:

* Maintains interval structures incrementally
* Reuses previous computations when intervals change
* Supports dynamic updates during search

This module is the primary low level solver used by the JointTAP framework.

#### 4. AssistanceOTP

**Files:** `assistance_otp.h`, `assistance_otp.cpp`

Contains the [original implementation](https://github.com/eitanbloch/TAP/) of the AssistanceOTP (Originally, OPTP) solver, with minor adaptations and bug fixes.

---

## Build Instructions

Using CMake:

```bash
mkdir build
cd build
cmake ..
make
```
