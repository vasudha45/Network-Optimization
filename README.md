1. Data Collection & Preprocessing
Installed required libraries: numpy, pandas, matplotlib, seaborn, gym, torch, stable-baselines3, ns3gym, scikit-learn.
Loaded datasets:
Throughput.csv
RoundTripTimes.csv
car-driving-trace-1.csv
car-driving-trace-2.csv
walking-trace.csv
Checked for non-numeric values and missing data.
Converted numeric columns and filled missing values with the column mean.
Encoded categorical columns (protocol, carrier, server_location, etc.).
Normalized throughput and RTT values using MinMaxScaler.
Saved preprocessed datasets.
2. Feature Engineering
Extracted time-based features (hour, day_of_week, is_weekend).
Created network congestion indicators:
Marked high throughput (> 75th percentile).
Marked high RTT (> 75th percentile).
Created a combined network_congestion indicator.
3. Reinforcement Learning Environment Creation
Defined a custom Gym environment (NetworkOptimizationEnv) for network optimization:
Actions: Improve throughput or RTT.
State: Random sample from throughput data.
Reward: Difference between throughput and RTT.
4. Training a Reinforcement Learning Model
Created a PPO (Proximal Policy Optimization) agent with stable-baselines3.
Trained the model for 100,000 timesteps.
Saved and tested the model.
Compared throughput before and after optimization using Matplotlib plots.
5. Hyperparameter Optimization with Optuna
Used Optuna to tune:
learning_rate
batch_size
gamma
Evaluated different configurations based on model performance.
Plotted the hyperparameter impact on rewards.
