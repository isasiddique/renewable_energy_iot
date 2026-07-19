📘 Code Explainer: Streaming Telemetry Physics Engine

This document breaks down the physical properties and math logic used in the turbine sensor script for non-technical stakeholders.

1. Simulating Physical Aerodynamics

np.random.uniform(0, 30): This simulates raw continuous data streaming from a turbine's anemometer wind velocity sensor, measuring wind speeds from completely dead air (0 m/s) to extreme storm gusts (30 m/s).
power_mw = 0.5 * 1.225 * (wind_speed_mps ** 3) * 0.45 / 10000: This line implements core atmospheric physics. Kinetic wind power output increases as a cubic function of wind velocity, meaning small increases in wind create exponentially larger physical force on the turbine gears.
np.where(wind_speed_mps > 25, 0.0, power_mw): This models structural hardware emergency boundaries. If ambient wind speeds exceed 25 m/s, real-world operators immediately deploy the mechanical brakes, stopping rotation to prevent the internal generator from catching fire or spinning out of control.
2. Segmenting Mechanical Wear

pd.cut(..., bins=bins, labels=labels): This categorizes continuous blade pitch telemetry into three distinct physical operating postures (Optimal, Friction, and Stalled), helping platform engineers isolate exactly how hardware alignment angles destroy financial power grid output.
