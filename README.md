[**English**](README.md) | [中文](README_CN.md)

# A Benchmark for Robotic Milling in Restricted Spaces

A standardized benchmark task for evaluating posture planning algorithms in restricted-space robotic milling scenarios.

## Overview

When machining large and geometrically complex components, industrial robots may be required to operate in restricted spaces — such as propeller blade root overlaps, turbine blade channels, and aerospace cabin inner walls — which pose significant challenges to conventional posture planning methods. This repository provides a **publicly available, reproducible benchmark geometry** for the systematic evaluation and comparison of robotic milling posture planning algorithms under representative restricted-space conditions.

The benchmark is designed as an **irregular semi-enclosed workspace** with all asymmetrically inclined obstacle features, forcing the robot to continuously adjust its multi-dimensional milling posture throughout the machining process. Notably, traditional single-dimensional (redundancy-angle-only) planning strategies yield **no feasible trajectories** in this scenario, thereby enforcing the necessity of multi-dimensional posture planning.

## Benchmark Specifications

| Parameter | Value |
|-----------|-------|
| Restricted space dimensions (excluding auxiliary supports) | 1.30 m × 0.96 m × 1.03 m |
| Machining trajectory | 1.3 m long horizontal straight path |
| Discrete CC point spacing | 2 mm |
| Obstacle configuration | Irregular semi-closed area with all inclined features |
| Robot system (as used in the original study) | ABB IRB-6660 |
| Milling spindle (as used in the original study) | HITECO |
| Tool (as used in the original study) | Fillet end mill, R = 12.5 mm, r = 5 mm |

> **Note:** While the original experimental validation was conducted on an ABB IRB-6660 system, this benchmark geometry is **robot-agnostic** and can be used with any 6-DOF industrial robot for posture planning algorithm evaluation.

## Design Rationale

The benchmark geometry is constructed with the following design principles:

- **Representativeness**: The irregular semi-enclosed structure references real-world restricted-space scenarios commonly encountered in the machining of propeller blade root overlaps and turbine blade channels.
- **Asymmetric obstacles**: All obstacle surfaces are asymmetrically inclined, ensuring that the feasible posture solution space changes dynamically along the toolpath rather than remaining static.
- **Multi-directional restriction**: The robot system is simultaneously restricted by surrounding obstacles from the left, right, and top directions, resulting in an extremely narrow and dynamically varying feasible solution space.
- **Reproducibility**: The geometry is provided in multiple standard CAD formats, enabling exact reproduction of the benchmark environment across different research groups and software platforms.

## File Description

| File | Format | Description |
|------|--------|-------------|
| `SDG1V7sim350_400E1.SLDPRT` | SolidWorks Part | Native CAD source file for editing and feature-level access |
| `SDG1V7sim350_400E1.STEP` | STEP (ISO 10303) | Platform-independent CAD exchange format; recommended for simulation environments |
| `SDG1V7sim350_400E1.STL` | STL Mesh | Triangulated surface mesh for collision detection and visualization |
| `SDG1V7sim350_400E1.STEP.pdf` | PDF Drawing | 2D drawing with dimensions for quick visual reference |

**Recommended usage:** Import the `.STEP` file into your robotic simulation environment (e.g., RoboDK, MATLAB Robotics Toolbox, CoppeliaSim, or custom simulation platforms) as the obstacle geometry for posture planning evaluation.

## How to Use This Benchmark

1. **Set up the restricted-space environment**: Import the obstacle geometry file into your simulation platform and position it according to the coordinate system defined in the original paper.
2. **Define the machining task**: A 1.3 m long horizontal straight trajectory is placed within the restricted space with a 2 mm discrete CC point spacing (651 cutter contact points).
3. **Run your posture planning algorithm**: Evaluate whether your algorithm can generate a feasible and continuous posture trajectory that avoids all obstacles throughout the entire machining process.
4. **Evaluate and compare**: Suggested evaluation criteria include:
   - **Feasibility**: Can the algorithm find a collision-free posture trajectory?
   - **Smoothness**: How smooth are the joint motions along the planned trajectory?
   - **Machining performance**: What are the stiffness, accuracy, or stability characteristics of the planned postures?
   - **Computational efficiency**: How long does the algorithm take to compute the solution?

## Citation

If you use this benchmark in your research, please cite the following paper:

```bibtex
@article{Su2026PotentialNetwork,
  title   = {Investigation of the 3D-posture planning for space-restricted robotic milling: A potential network architecture},
  author  = {Su, Juntong and Zhao, Shengqiang and Peng, Fangyu and Tang, Xiaowei and Yan, Rong},
  journal = {International Journal of Machine Tools and Manufacture},
  volume  = {215},
  pages   = {104364},
  year    = {2026},
  doi     = {10.1016/j.ijmachtools.2026.104364}
}
```

This benchmark is also referenced in the following review paper:

```bibtex
@article{Su2026Review,
  title   = {Towards next-generation intelligent robotic machining: Constraint-aware modeling and posture planning — A comprehensive review},
  author  = {Su, Juntong and others},
  journal = {Journal of Manufacturing Systems},
  year    = {2026},
  note    = {Under review}
}
```

## License

This benchmark is provided for **academic and research purposes**. If you use or adapt this geometry in your work, please cite the original paper listed above.

## Contact

For questions, suggestions, or collaboration inquiries, please open an issue on this repository or contact the corresponding author via the information provided in the cited paper.
