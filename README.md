# Advanced PPO for Quadruped Locomotion in Isaac Lab

This repository showcases the development and enhancement of a Proximal Policy Optimization (PPO) agent for training a quadruped robot. The project leverages the high-fidelity NVIDIA Isaac Lab simulation environment and the RSL-RL library to teach complex walking behaviors.

The core of this work involves a systematic, from-scratch implementation and enhancement of the PPO algorithm, demonstrating a deep understanding of both reinforcement learning theory and high-performance code.

## Project Overview
The goal of this project is to train a high-performing locomotion policy for an ANYmal-C quadruped robot. Starting with the foundational rsl_rl library, this work dissects the standard PPO algorithm and rebuilds it step-by-step. The final result is a custom agent incorporating state-of-the-art techniques that successfully matches the performance of the highly optimized, production-grade implementation.

### Key Objectives:
- Implement PPO from First Principles: Re-create the core PPO algorithm to gain a deep understanding of its components, including the clipped surrogate objective, value function loss, and advantage estimation.
- Systematic Enhancement: Incrementally add advanced, state-of-the-art techniques to the baseline PPO to improve its performance and stability.
- Rigorous Analysis: Use TensorBoard to conduct comparative experiments, validating the impact of each algorithmic enhancement against the baseline and the original library implementation.

## Algorithmic Contributions
This project's main contribution is the step-by-step implementation of a PPO agent, validating the impact of several key techniques:

### 1. Foundational PPO Implementation
A baseline PPO agent was built from scratch, including:
- The core PPO clipped surrogate objective, value objective, and regularized entropy term.
- Essential stability tricks such as advantage normalization, clipped value loss, and gradient clipping.

### 2. Adaptive Learning Rate Schedule
To improve stability and convergence speed, a KL-adaptive learning rate schedule was implemented.
- The learning rate is dynamically adjusted based on the KL-divergence between the old and new policies.
- This allows the agent to take larger, more confident steps when the policy is stable and smaller, more cautious steps during periods of high change, preventing training collapse.

## Repository Structure
To showcase the work clearly, this repository contains:
- /results: Contains screenshots of TensorBoard graphs and videos of the trained agent's performance.
- README.md: This file.
- The modified PPO algorithm lives in a fork of the rsl_rl library, which can be found here: https://github.com/huangfq07/rsl_rl

## Setup & Usage
This project builds upon the NVIDIA Isaac Lab ecosystem.
1. Setup Isaac Lab: Follow the official Isaac Lab installation documentation to set up the simulator and the conda environment.
2. Install Modified RSL-RL: To use the custom PPO agent, install it from the forked repository.
```
# Activate the conda environment
conda activate env_isaaclab

# Install the modified library directly from your forked GitHub repo
pip install git+https://github.com/huangfq07/rsl_rl.git
```
3. Run Training: Launch the training script using the provided Isaac Sim python environment. Remember to source the setup script first.
```
# From a new terminal
conda activate env_isaaclab
source /path/to/isaac_sim/setup_conda_env.sh

# Run the training script from the IsaacLab directory
./isaaclab.sh -p scripts/reinforcement_learning/rsl_rl/train.py --task=Isaac-Velocity-Flat-Anymal-C-v0 --headless
```
Visualize Results:
```
tensorboard --logdir logs/rsl_rl
```
