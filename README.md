# SRNetwork Hyperparameters and Results v0

This repository contains comprehensive experimental configurations and results for my thesis research on A Neural Network Model for Symbolic Regression and Scientific Discovery v0. The work explores two distinct approaches: parameter fitting for pre-specified function structures and full symbolic regression framework training.

## Repository Structure

```
├── parameter_fitting/          # Parameter fitting experiments
│   ├── configs/                # Configuration files for experiments
│   │   └── nguyen_configs/     # Nguyen benchmark configurations
│   └── results/                # Experimental results and outputs
│       └── nguyen_fit/                # Parameter fitting results
├── sr_framework/               # Full symbolic regression framework
├── data/                       # Dataset storage
└── LICENSE                     # MIT License
```

## Experimental Approaches

### 1. Parameter Fitting (`parameter_fitting/`)

In this approach, function structures are pre-specified and the neural network learns to fit the parameters of these known mathematical expressions. This method focuses on:

- **Function Structure**: Known mathematical forms (e.g., polynomials, trigonometric functions)
- **Parameter Optimization**: Neural network learns coefficients and exponents
- **Benchmark Testing**: Evaluation on standard Nguyen benchmark problems
- **Post-processing**: L-BFGS optimization for fine-tuning

**Key Features:**
- Configuration-driven experiments using YAML files
- Support for various function sets including SafeExp, SafeLog, SafeSin, SafePower
- Reward tracking with NRMSE metrics
- Checkpointing and model persistence
- Automated plotting and visualization

### 2. Full Symbolic Regression Framework (`sr_framework/`)

This approach implements end-to-end symbolic regression where the network simultaneously learns both the mathematical structure and parameters. Features include:

- **Structure Search**: Discovery of mathematical expressions from scratch
- **Joint Training**: Simultaneous learning of structure and parameters
- **Exploration**: Search through the space of possible mathematical expressions

## Configuration System

Experiments are configured through YAML files that specify:

```yaml
# Model architecture 
model:
  input_size: 1
  output_size: 1
  num_layers: 2
  nonlinear_info: [[3, 0], [0, 0], [0, 0]]
  function_set: ["SafeIdentityFunction", "SafeExp", "SafeLog", "SafeSin", "SafePower"]

# Training parameters
training:
  num_epochs: 1000
  batch_size: 32
  learning_rate: 1.0
  optimizer: "adamw"
  scheduler: "cosine"

# Loss configuration
loss:
  type: "mse"
  use_derivatives: false

# L-BFGS post-optimization
lbfgs:
  enabled: true
  max_iterations: 1000
  tolerance: 1e-8
```

## Benchmark Problems

The repository includes configurations and results for the Nguyen benchmark suite:

- **Nguyen-1 through Nguyen-12**: Standard symbolic regression benchmarks
- **Variants**: Different configurations for multi-dimensional problems
- **Comparative Analysis**: Performance across different hyperparameter settings

## Results and Metrics

Each experiment generates comprehensive outputs:

- **Equation Discovery**: Final mathematical expressions
- **Performance Metrics**: MSE, RMSE, MAE evaluation
- **Training Dynamics**: Reward evolution and loss curves
- **Visualizations**: Plots of discovered functions vs. true functions
- **Optimization History**: L-BFGS refinement results

## Key Files

### Configuration Files
- `nguyen_configs/*.yaml`: Hyperparameter settings for each benchmark problem
- Each config specifies model architecture, training parameters, and optimization settings

### Results
- `*/results.json`: Complete experimental metadata and performance metrics
- `*_equation.txt`: Discovered mathematical expressions
- `*_plot.png`: Visualization of fitted functions
- `*_reward_evolution.png`: Training progress visualization

## Usage

The configurations in this repository can be used to:

1. **Reproduce Results**: Re-run experiments with identical hyperparameters one the model is published
2. **Hyperparameter Studies**: Analyze the impact of different settings
3. **Benchmarking**: Compare against these baseline results
4. **Extension**: Adapt configurations for new problems or datasets

## Technical Details

### Model Architecture
- Configurable neural network depth and width
- Support for various activation functions
- Dropout regularization options
- Connectivity pattern specifications

### Optimization
- Multiple optimizer support (Adam, AdamW, SGD)
- Learning rate scheduling (cosine, cyclic)
- L1 regularization for sparsity
- Two-stage optimization (neural network + L-BFGS)

### Evaluation
- Multiple loss functions (MSE, CVaR, TopK)
- Derivative constraints support
- Reward-based training with NRMSE metrics
- Comprehensive checkpoint management

## Data Requirements

Experiments expect data in specific formats:
- Input features and target values
- Support for train/validation splits
- Configurable uncertainty values for noisy data

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Citation

If you use these configurations or results in your research, please cite the associated thesis work on symbolic regression using neural networks.

---

*This repository represents experimental work conducted as part of thesis research on neural symbolic regression methods. The configurations and results provide insights into hyperparameter sensitivity and performance characteristics across standard benchmark problems.*
