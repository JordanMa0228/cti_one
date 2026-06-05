# W102 Path Planning Simulation

This repository contains a simple ROS2 Python package for a 2D top-down path-planning simulation for robot W102 in a living room with a chair obstacle between the robot and the user John.

## Package

- `w102_path_planning`

## Node

- `w102_path_sim.py`

## Scenario Setup

- Room size: 10 ft × 12 ft
- Start position `S`: `(0, 0)`
- Chair obstacle center: `(0, 4)`
- Goal position `G` (John): `(0, 10)`
- Robot footprint: approximately `2.25 ft × 2.67 ft`
- Inflated obstacle safety margin: `1.75 ft`

## Graph Nodes

- `S  = (0, 0)`
- `L1 = (-3, 0)`
- `L2 = (-3, 6)`
- `R1 = (3, 0)`
- `R2 = (3, 6)`
- `G  = (0, 10)`

## Edges

- `S -> L1`
- `L1 -> L2`
- `L2 -> G`
- `S -> R1`
- `R1 -> R2`
- `R2 -> G`

Using Euclidean edge cost:

- `S -> R1 = 3 ft`
- `R1 -> R2 = 6 ft`
- `R2 -> G = 5 ft`
- Total right path cost = `14 ft`

The left path has the same total cost. The direct path from `S` to `G` is treated as blocked because it intersects the inflated chair obstacle region.

## Chosen Final Trajectory

The simulation uses the right-side path as the final trajectory:

`(0,0) -> (3,0) -> (3,6) -> (0,10)`

## Deliverables

The node generates the following inside `results/`:

- `trajectory_result.png`
- `trajectory_points.csv`
- `README.md`
- optional `w102_simulation.gif`

## Requirements

- Ubuntu 24.04
- ROS 2 Kilted
- Python 3
- `rclpy`
- `numpy`
- `matplotlib`

## Run

After building your workspace:

```bash
ros2 run w102_path_planning w102_path_sim
```
