This repository contains a Kalman filter implementation for smoothing GPS-derived elevation data. The filter was used as part of a participatory topographic data collection workflow, where elevation points were collected using GPS-enabled mobile devices.
GPS elevation measurements can contain considerable noise and short-term fluctuations. These variations may not represent actual changes in ground elevation and can affect the quality of a Digital Elevation Model (DEM) generated from the collected points.
The Kalman filter is therefore applied to reduce measurement noise and produce a smoother elevation profile while retaining the underlying variation in the terrain.

Why use a Kalman filter?
GPS-based elevation measurements are affected by measurement uncertainty. Even when a participant is moving over relatively uniform terrain, the recorded elevation can fluctuate between consecutive observations.
For example:
Raw GPS elevation:
100.2  →  100.8  →  99.9  →  101.1  →  100.4
Filtered elevation:
100.2  →  100.4  →  100.3  →  100.5  →  100.5
The purpose of the filter is not to remove genuine changes in elevation, but to reduce rapid fluctuations that are likely to be caused by GPS measurement noise.
The resulting elevation data can then be used as input points for subsequent DEM generation.

How the Kalman filter works?
The implementation treats elevation as a time-varying variable and estimates the most likely elevation at each observation.
For each measurement, the filter performs two main steps:
1.Prediction
2.Measurement update

1. Prediction step
The filter first predicts the current elevation based on the previous estimate.
2. Measurement update
The predicted elevation is then compared with the new GPS elevation measurement.
