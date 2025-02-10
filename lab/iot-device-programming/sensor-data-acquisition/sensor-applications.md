# Sensor Applications

## **Tilt-Based Interaction**

**Objective:** Use the onboard Gyroscope (LSM6DS33) to detect tilting in different directions and trigger corresponding actions.

1. Read acceleration values.
2. Define threshold values to detect tilts in the X and Y directions.
3. Print messages based on tilt direction:
   * Left tilt → "Tilted Left!"
   * Right tilt → "Tilted Right!"
   * Forward tilt → "Tilted Forward!"
   * Backward tilt → "Tilted Backward!"
4. Instead of printing messages, map tilt direction to onboard NeoPixel colours.

## **Gesture-Based Control with APDS9960**

**Objective:** Use the gesture sensor (APDS9960) to recognize hand movements and trigger different actions.

1. Enable gesture detection.
2. Read gesture inputs.
3. Print detected gestures:
   * Left swipe → "Left Gesture Detected!"
   * Right swipe → "Right Gesture Detected!"
   * Up swipe → "Up Gesture Detected!"
   * Down swipe → "Down Gesture Detected!"

## **Digital Compass with Visual Feedback**

**Objective:** Use the magnetometer (LIS3MDL) to determine orientation and display cardinal directions.

1. Read magnetometer data.
2. Compute heading using `math.atan2(mag_y, mag_x) * (180 / math.pi)`.
3. Print the corresponding cardinal direction:
   * 0° to 45° → "North"
   * 45° to 135° → "East"
   * 135° to 225° → "South"
   * 225° to 315° → "West"
4. If using a NeoPixel, change its colour based on the direction.
5. Add a small hysteresis to avoid flickering between directions.

## **Silent Clap Detector (Sound Level Spike Detection)**

**Objective:** Detect sudden increases in microphone sound level and print a message when a "clap" is detected.

1. Read microphone RMS values using `normalized_rms(samples)`.
2. Set a threshold for detecting a sharp increase in amplitude.
3. Print "Clap detected!" when the threshold is exceeded.
4. Implement a double clap detector by checking if two claps occur within 1 second.

## **Vibrations Detector using Accelerometer**

**Objective:** Use the accelerometer to detect a strong tap or knock on the board.

1. Continuously read acceleration values.
2. Detect sudden spikes in acceleration above a defined threshold.
3. Print "Knock detected!" when a knock is detected.
4. Count and display the number of knocks detected within a given time frame.
