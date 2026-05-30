# EE 471 Final Project

## Comparison of Stanley and Pure Pursuit Path Tracking Controllers in CARLA

### Team Members

* Gulianna Corteguera
* Maddie Masiello

---

# Project Overview

This project compares two common autonomous vehicle path tracking algorithms:

1. Stanley Controller
2. Pure Pursuit Controller

The controllers are implemented in the CARLA simulator and evaluated using multiple road geometries and controller tuning parameters.

Performance is evaluated using:

* Cross-track error
* Heading error
* Trajectory tracking
* Final distance to goal
* Controller tuning sensitivity

---

# Project Objectives

The goal is to determine how Stanley and Pure Pursuit perform under different driving scenarios and tuning parameters.

The project investigates:

* Straight road tracking
* Curved road tracking
* Complex turning road tracking

and compares:

Stanley gains:

* k = 0.4
* k = 0.8
* k = 1.2

Pure Pursuit lookahead distances:

* 3 m
* 6 m
* 10 m

---

# Folder Structure

## results/

Contains CSV data generated from all experiments.

Example:

stanley_straightline_k08.csv

purepursuit_ccurve_ld6.csv

Each file contains:

* Vehicle position
* Steering commands
* Cross-track error
* Heading error
* Distance to goal
* Simulation time

---

## plots/

Contains figures generated from the experimental results.

Example:

trajectory_straightline.png

cross_track_error_ccurve.png

stanley_gain_sweep_sturn.png

summary_metrics.csv

---

# Python Files

## path_tracking_experiments.py

Main experiment script.

Automatically:

1. Loads CARLA
2. Generates road-following reference paths
3. Runs Stanley controller experiments
4. Runs Pure Pursuit experiments
5. Saves all CSV files

This is the primary script used for data collection.

---

## plot_full_experiments.py

Generates publication-quality figures from the CSV data.

Creates:

* Trajectory plots
* Cross-track error plots
* Heading error plots
* Stanley gain sweep plots
* Pure Pursuit lookahead sweep plots
* Summary metrics table

---

## stanley_test.py

Early implementation and testing of the Stanley controller.

Used to validate:

* Steering commands
* Path following
* Data logging

---

## purepursuit_test.py

Early implementation and testing of the Pure Pursuit controller.

Used to validate:

* Lookahead target selection
* Steering commands
* Data logging

---

## list_maps.py

Utility script that lists available CARLA maps.

---

# Experimental Design

Three road types are evaluated:

## Straightline

Road segment with minimal heading change.

Purpose:

Evaluate controller behavior on an easy path.

---

## C-Curve

Road segment with mostly one-direction curvature.

Purpose:

Evaluate controller behavior on a sustained turn.

---

## S-Turn

Road segment with multiple changes in turning direction.

Purpose:

Evaluate controller performance on a challenging route.

---

# Controllers

## Stanley Controller

Uses:

* Heading error
* Cross-track error

Steering law:

delta = heading_error - atan(k * cross_track_error / speed)

Advantages:

* Strong path convergence
* Low cross-track error

Potential drawbacks:

* Sensitive to gain selection
* Can oscillate at high gain values

---

## Pure Pursuit Controller

Uses:

* Lookahead target point

Steering is based on the angle to the target point.

Advantages:

* Smooth behavior
* Simple implementation

Potential drawbacks:

* Corner cutting
* Larger tracking error with large lookahead distances

---

# Running the Project

## Step 1

Launch CARLA simulator.

---

## Step 2

Run all experiments.

python path_tracking_experiments.py

---

## Step 3

Generate figures.

python plot_full_experiments.py

---

# Deliverables

The project produces:

* Experimental CSV datasets
* Trajectory plots
* Cross-track error plots
* Heading error plots
* Parameter sweep plots
* Summary metrics table


