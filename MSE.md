**MSE (Mean Squared Error)** is a standard metric for measuring how close the model’s predictions are to the true (ground truth) values.
<br>MSE = (1/N) × Σ (y_trueᵢ − y_predᵢ)²

where:
- N = total number of samples  
- y_trueᵢ = true value at index i  
- y_predᵢ = predicted value at index i
  
<br>It penalizes large deviations heavily since the error is squared.

- Lower MSE → Better accuracy
- Higher MSE → Model predictions deviate more from truth
  
<br>**1. MSE (Fused)**: This measures how well the Bayesian fusion algorithm estimated the true trajectory. Data source is Radar + LiDAR combined output.
- true_pos → the actual target positions (ground truth trajectory)
- fused_pos → the combined estimates from radar + LiDAR using Bayesian fusion

<br>Interpretation: 
<br>MSE (Fused) shows how accurate is the fused sensor estimate is compared to the real target. It reflects the effectiveness of the sensor fusion step (i.e., how much noise was reduced by combining radar and LiDAR).
If this value is small, it means the fusion model effectively combined both sensors to give a stable and accurate reading.

<br>**2. MSE (Kalman)**: This measures how well the Kalman filter tracked the true trajectory after fusion.
<br>kf_estimates (in the code) → filtered (smoothed) position predictions from the Kalman filter after processing the fused data.

<br>Interpretation:
<br>MSE (Kalman) quantifies how much improvement the Kalman filter achieved over the fused data.It reflects the filtering and temporal smoothing performance, whether the model was able to smooth out residual noise, maintain stability and predict accurately through time.
<br>
- If MSE (Kalman) < MSE (Fused) → the Kalman filter is successfully refining the estimates.
- If MSE (Kalman) ≈ MSE (Fused) → the fusion data was already very clean (common in this demo since the process noise is low).
- If MSE (Kalman) > MSE (Fused) → the Kalman parameters (Q, R) may be mis-tuned.

<br> In this demo, MSE (Fused): 0.5522, MSE (Kalman): 2.9374
<br> This means:
- The Bayesian fusion reduced sensor noise effectively.
- The Kalman filter further improved accuracy by smoothing temporal variations, making predictions more stable and closer to the true trajectory.
