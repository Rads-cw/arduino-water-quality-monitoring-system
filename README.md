# Water Quality Monitoring System

An Arduino-based water quality monitoring system that measures TDS, turbidity, temperature, and water level in real time.

The system processes sensor readings, displays the results on an LCD, provides LED and buzzer alerts, and sends data to the Arduino IoT Cloud for remote monitoring. :contentReference[oaicite:0]{index=0}

## Features

- Real-time TDS monitoring
- Turbidity measurement and classification
- Water temperature measurement
- Water level detection
- LCD display
- LED status indicators
- Buzzer warning system
- Arduino IoT Cloud integration
- Sensor filtering and averaging
- Temperature compensation for TDS readings

## Components

- Arduino board
- TDS sensor
- Turbidity sensor
- DS18B20 temperature sensor
- Water level sensor
- I2C LCD
- LEDs
- Buzzer
- Breadboard
- Jumper wires

The project combines all of these components into one monitoring system. :contentReference[oaicite:1]{index=1}

## How It Works

The Arduino reads data from the connected sensors and processes each measurement.

The system monitors:

- TDS
- Turbidity
- Temperature
- Water level

Temperature compensation is applied to the TDS reading to improve stability.

The turbidity sensor reading is converted into a percentage and classified as:

- CLEAR
- CLOUDY
- DIRTY

The water level is classified as:

- LOW
- MEDIUM
- HIGH
- No water

The LCD switches between sensor readings every three seconds. :contentReference[oaicite:2]{index=2}

## Pin Configuration

| Component | Pin |
|---|---|
| Temperature Sensor | D5 |
| TDS Sensor | A1 |
| Turbidity Sensor | A0 |
| Water Level Sensor | A2 |
| High Level LED | D2 |
| Medium Level LED | D3 |
| Low Level LED | D4 |
| No Water LED | D6 |
| Buzzer | D8 |

## TDS Processing

The TDS sensor is connected to analog pin A1.

The program collects 10 ADC samples, sorts them, removes the two highest and two lowest values, and averages the remaining samples.

Temperature compensation is then applied before calculating the final TDS value.

This filtering helps reduce instability caused by sensor noise and ADC fluctuations. :contentReference[oaicite:3]{index=3}

## Turbidity Classification

The turbidity sensor is connected to analog pin A0.

The analog reading is converted into a percentage and classified as:

| Turbidity | Status |
|---|---|
| Below 20% | CLEAR |
| 20% to below 50% | CLOUDY |
| 50% or higher | DIRTY |

:contentReference[oaicite:4]{index=4}

## Water Level Detection

The water level sensor is connected to analog pin A2.

The detected water level is classified using the following ranges:

| Sensor Reading | Status |
|---|---|
| 100–310 | LOW |
| 311–440 | MEDIUM |
| 441–700 | HIGH |
| Outside these ranges | No water |

:contentReference[oaicite:5]{index=5}

## Warning System

A buzzer is used to warn the user when abnormal readings are detected.

The warning is triggered when:

- TDS is 400 ppm or higher
- Turbidity is 50% or higher

The buzzer produces two short beeps followed by one longer beep.

A three-second cooldown prevents the buzzer from triggering continuously. :contentReference[oaicite:6]{index=6}

## LCD Display

The LCD alternates between two screens every three seconds.

### Screen 1
- TDS value
- TDS status
- Turbidity percentage
- Turbidity status

### Screen 2
- Temperature
- Water level

:contentReference[oaicite:7]{index=7}

## Arduino IoT Cloud

The project uses Arduino IoT Cloud to provide remote monitoring of the sensor readings.

The Arduino continuously updates the cloud connection and synchronizes the monitored variables. :contentReference[oaicite:8]{index=8}

## Challenges

Some of the main challenges during development included:

- Sensor reading instability
- Noise in analog measurements
- Integrating multiple sensors on one Arduino
- Different sensor timing requirements
- Combining LCD output with cloud communication

Filtering, averaging, and temperature compensation were used to improve measurement stability. :contentReference[oaicite:9]{index=9}

## Applications

Possible applications include:

- Drinking water monitoring
- Aquaculture and fish farms
- Industrial water management
- River and lake monitoring

:contentReference[oaicite:10]{index=10}

## Future Improvements

Possible future improvements include:

- Adding a pH sensor
- Improving sensor calibration
- Adding automatic alerts
- Improving wireless monitoring
- Adding historical data visualization
