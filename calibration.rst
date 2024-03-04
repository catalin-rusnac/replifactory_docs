Device Calibration
==================

This document outlines the steps for calibrating peristaltic pumps, stirrers, and optical density (OD) sensors in your device. Proper calibration ensures accurate operation and measurement during experiments.

Enter Calibration Mode
----------------------

To start the calibration process, activate calibration mode by toggling the switch located in the top right corner of the Device page.

Pump Calibration
----------------

The goal of pump calibration is to determine the accurate volume per rotation at different operational speeds. Due to the nature of peristaltic pumps, the volume pumped can vary with speed. Follow these steps for each pump:

**1. Prepare for Calibration:** Ensure the tubing is filled with liquid (not air) throughout its entire section to avoid inaccurate measurements.

**2. Measure Volume:** Conduct the following sequences and measure the pumped volume after each.

- 50 sequences of 1 rotation
- 10 sequences of 5 rotations
- 5 sequences of 10 rotations
- 1 sequence of 50 rotations

**3. Record measurements:** Place a vial on a precision scale near the device edge. Open the corresponding valve and execute the calibration sequences. The app will calculate the mL/rotation coefficient for each volume.


You can measure the volume by placing the first or last vial (closer to the edge) on a small scale near the device, opening the corresponding valve and pumping the calibration sequence. The app will calculate the mL/rotation coefficient for each point and use these values to accurately pump both small (~0.1mL) and large volumes (>10mL).

Stirrer Calibration
-------------------

Proper stirrer calibration is essential for effective mixing and accurate OD measurement. Calibration ensures the stirrer operates at optimal speeds for different conditions:

**High Speed**: Achieve good mixing without causing the stirrer bar to detach and rattle.

**Low Speed**: Gently stir the culture without forming a vortex that could interfere with the laser path during OD measurements.

.. tip:: To toggle all stirrers simultaneously, double-click the buttons.

OD Sensor Calibration
---------------------
OD sensors measure culture density by quantifying the amount of light that passes through the culture. The sensors use a photodiode to measure the light intensity, which is then converted to an optical density (OD) value. The OD value is a measure of the culture's turbidity, or the amount of light that is absorbed or scattered by the culture. The OD value is directly proportional to the culture's cell density, making it a useful metric for monitoring cell growth.

.. note:: If OD probes are not provided, you can calibrate the OD sensors using probes made of paper or translucent plastic. To create a probe, follow these steps:

    1. Insert a sheet of translucent material (e.g. paper) in the OD sensor, about 3mm from the photodiode. Use the vial clips to hold the paper in place.
    2. Measure the signal in one of the OD sensors.
    3. Remove the sheet of paper and insert a vial of medium in the holder.
    4. Slowly increase the turbidity (e.g. with milk) of the medium while measuring the signal in the sensor.
    5. When the signal reaches the same value - measure the OD of the turbid medium with a spectrophotometer.
    6. Label the sheet of paper with this OD value - now we know that inserting a paper in the sensor produces a signal equivalent to a culture with this OD.
    7. Repeat the process with 2,3,4 papers - label all of the probes with increasing OD values, as measured by the spectrophotometer. You can use these probes to calibrate all OD sensors in all devices.

.. warning:: Cut the paper probes so they fit inside the device without bending at the edges near vial 1 and vial 7 - the paper has to be very close to the photodiode.

For every probe:

1. Insert the probe in front of the photodiode
2. Insert the probe OD value in the text field near the green “Measure new probe” button
3. Press the “Measure new probe” button. Watch how this affects the calibration curves for each OD sensor.

.. tip:: You can edit and remove individual data points as well as entire rows.