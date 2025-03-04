**INTRODUCTION:**
This project focuses on optimizing network performance using reinforcement learning. It begins with data collection and preprocessing, where various datasets containing throughput, round-trip time (RTT), and mobility traces are cleaned, normalized, and enriched with time-based and congestion-related features. A custom reinforcement learning environment is then designed to improve network performance by dynamically optimizing throughput and latency. The **Proximal Policy Optimization (PPO)** algorithm is trained to make intelligent decisions based on real-time network conditions. To enhance model performance, **Optuna** is used for hyperparameter tuning, refining parameters like learning rate, batch size, and discount factor. The project integrates **machine learning, reinforcement learning, and real-world network optimization**, making it a comprehensive approach to improving communication networks.

**1. Data Collection & Preprocessing**
- Installed required libraries: `numpy`, `pandas`, `matplotlib`, `seaborn`, `gym`, `torch`, `stable-baselines3`, `ns3gym`, `scikit-learn`.
- Loaded datasets:
  - `Throughput.csv`
  - `RoundTripTimes.csv`
  - `car-driving-trace-1.csv`
  - `car-driving-trace-2.csv`
  - `walking-trace.csv`
- Checked for non-numeric values and missing data.
- Converted numeric columns and filled missing values with the column mean.
- Encoded categorical columns (`protocol`, `carrier`, `server_location`, etc.).
- Normalized throughput and RTT values using `MinMaxScaler`.
- Saved preprocessed datasets.

**2. Feature Engineering**
- Extracted time-based features (`hour`, `day_of_week`, `is_weekend`).
- Created network congestion indicators:
  - Marked high throughput (`> 75th percentile`).
  - Marked high RTT (`> 75th percentile`).
  - Created a combined `network_congestion` indicator.

**3. Reinforcement Learning Environment Creation**
- Defined a **custom Gym environment** (`NetworkOptimizationEnv`) for network optimization:
  - Actions: Improve throughput or RTT.
  - State: Random sample from throughput data.
  - Reward: Difference between throughput and RTT.

**4. Training a Reinforcement Learning Model**
- Created a `PPO` (Proximal Policy Optimization) agent with `stable-baselines3`.
- Trained the model for `100,000` timesteps.
- Saved and tested the model.
- Compared throughput before and after optimization using Matplotlib plots.

**5. Hyperparameter Optimization with Optuna**
- Used Optuna to tune:
  - `learning_rate`
  - `batch_size`
  - `gamma`
- Evaluated different configurations based on model performance.
- Plotted the hyperparameter impact on rewards.


