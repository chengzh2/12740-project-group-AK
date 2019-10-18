![](img_url)
### Team Members

Yaxian Zheng, Cheng Zhang, Kaiwen Zhang, Yanbo Zhang

## Introduction
 
The Waking-up System for Rear Window Defogger is an automated anti-fog system. This system combines the fog detection, automatic activation of defogger and driver notice properties. The fog detection property is achieved by gathering air temperature in the vehicle and the temperature and humidity of rear window glass. The system can detect the formation of fog and activate the fan at the rear window and the buzzer alert the driver. The fan would stop as the rear window is cleared. Furthermore, the users can monitor the temperature and humidity change in their vehicles during a period on the website “OpenChirp”. 

### Motivation

Vehicle windshield fogging is considered as a potential safety problem. The presence of fog on the windshield blurs the window and blocks drivers’ vision. Especially in areas with cold winters, drivers are more likely to turn on the heaters, which result in fog on the inside of windows. A defogger plays an important role in clearing up the fogged windshield by blowing out warm air. Normally, the front window defogger is activated by drivers manually, as they noticed the formation of fog. However, the drivers rarely could notice the formation of fog on the rear window on time, because they pay more attention to the front. When deciding to make a turn or back up, they just realize the fog on the rear window. With blocked backward sight, accidents are likely to happen. 

The extreme cold and snowy winter in Pittsburgh cause more driving safety concerns than the warm area. Therefore, the Waking-up System for Rear Window Defogger can play a more crucial and practical role for traffic accident prevention.  

### Goals
The goal of this project is to justify the accessibility of fog detection and the automatic defogger in the system. The whole system is installed and tested inside a glass box. The final project can detect the fog on the glass wall by gathering the relative humidity and temperature on the glass. The automatic defogger can activate and stop as the numerical data reaches the threshold. Furthermore, the buzzer is capable to beep and stop as the overcomes the threshold. If the sensitivity and predictive capacity increase, the project may be able to apply to real vehicles. 

## Methodology

To defog on the rear window inner surface, the physical principles of fogging and methods to defog are explained. The sensors used to detect fog generation and signal processing are analyzed in this part.

### Phenomena of Interest

#### Physical Principles

The generation of fog on a surface usually can be contributed to the fact that the temperature of this surface has reached the dew point temperature of its surrounding air. The water vapor in the surrounding air consequently will condense on this surface. The cause of this phenomenon is that the surface temperature is largely lower than the surrounding temperature due to some specific reasons. For example, small dew generates on the beneath surface of grass in the morning. This is mainly because the cold ground continuously radiates to the surface beneath which results in the condensation of the surrounding air of grass. In the car window case, the humidity ratio in a car is usually at a high level since the breathing effects of humans. When the inner surface of the car window has a temperature lower than the dew point temperature of its surrounding air due to cold outside weather, fogging will occur on the inner surface. 

The methods of defogging usually are out of two principles. One of them is to decrease the water vapor content around the window. This can be accomplished by blowing cold air into the car since the cooling system in cars usually is combined with the function of drying air. The other method is to increase the temperature of windows to make it higher than the dew point temperature. To accomplish this purpose, warmer air can be blown to the surface to raise the temperature. This principle was chosen to conduct the following experiment.

These principles can be explained and directly shown in psychrometric chart. The schematic points on psychrometric chart are shown in Figure.1. As shown in Fig.1, when the inner surrounding air of the window is at 21℃, its corresponding dew point temperature can be 16℃ at a specific inner condition. Thus, when the temperature on the surface of window reaches the surrounding air’s dew point temperature, condensation will occur on the inner surface resulting in the fog on the window.



### Sensors Used

Regarding the principles discussed above, we will need sensors to detect the fog, alarm system to warn the driver when the fog generates and also the operating system to remove the fog. Finally, we will need to stop the defog system when the temperature is high enough and the fog is diminished. The detailed information of devices including principles and characteristics are described below. 

#### DHT11 Humidity and Temperature Sensor 

DHT11 sensor is used to detect the generation of fog. It has 3 pins and sends its temperature and relative humidity data to Raspberry Pi. We use DHT11 to judge the fog by the combined consideration of temperature and relative humidity. Its technical details are shown as following:

● Low cost
● 3 to 5V power and I/O
● 2.5mA max current use during conversion (while requesting data)
● Good for 20-80% humidity readings with 5% accuracy
● Good for 0-50°C temperature readings ±2°C accuracy
● No more than 1 Hz sampling rate (once every second)
● Body size 15.5mm x 12mm x 5.5mm
● 4 pins with 0.1" spacing

##### Principles of humidity measurement

The principle for the humidity measurement of DHT11 is to detect water vapor by measuring the electrical resistance between two electrodes. Between the electrodes, there is a moisture-holding substrate that can absorb water vapor. The substrate releases free ions, which increases the conductivity between the electrode, as water vapor enters it. Thus, the humidity sensing component is a moisture holding substrate with electrodes applied to the surface. When water vapor is absorbed by the substrate, ions are released by the substrate which increases the conductivity between the electrodes. The change in resistance between the two electrodes is proportional to the relative humidity. Higher relative humidity decreases the resistance between the electrodes, while lower relative humidity increases the resistance between the electrodes.

##### Principles of temperature measurement

The measurement of the temperature of DHT11 is finished by a surface mounted NTC temperature sensor built into the unit. This temperature sensor is one type of thermistors[3]. It measures the temperature by the resistance changing with temperature. Thermistors are made from semiconductor materials. The resistance of a thermistor is measured by applying a constant current, then measuring the resulting voltage and finally the determination of the RTD resistance. Thermistors exhibit a highly nonlinear resistance vs. temperature curve. Thus, in the thermistors operating range there exhibits a large resistance change for a very small temperature change. This makes for a highly sensitive device, ideal for set-point applications[4].

With the plastic housing removed, you can see the electrodes applied to the substrate, an IC mounted on the back of the unit converts the resistance measurement to relative humidity. It also stores the calibration coefficients and controls the data signal transmission between the DHT11 and the Arduino. Fig.2 shows the picture of the departed DHT11 sensor.

<div align="center">
<img width="550" height="350" src="https://user-images.githubusercontent.com/42809684/66973309-9c878100-f065-11e9-99c5-bf38f289d4d6.png"/></div>

<p align="center">Figure 2. Picture of DHT11<sup>[1]</sup></p>

#### Fan

The team use Noctua NF-R8 redux-1800 PWM cooling fan to react with the humidity increase and defog the window. This cooling fan is a 4-pin fan with a voltage of 12V. Its detailed characteristics are listed below [5]:

●	4-pin connector
●	Voltage of 12V
●	Max RPM:180/ Min RPM:325
●	Acoustical Noise of 17.1 dB(A)
●	Static Pressure of 1.41 mmH2O
●	Airflow of 53.3 m3/h
●	Body size of 80mm x 80mm x 25mm

#### Buzzer

The team use buzzer to warn drivers when the window is fogging. A buzzer can be sorted as a passive or active buzzer. An active buzzer has a built-in oscillating source. Thus, it will make sounds when electrified. But a passive buzzer does not have such a source, so it will not tweet if DC signals are used; instead, you need to use square waves whose frequency is between 2K and 5K to drive it. The active buzzer is often more expensive than the passive one because of multiple built-in oscillating circuits. Its detailed characteristics and connection information are shown below[2]:

●	Work Voltage:3.3-5V
●	PCB Dimension: 3.1cm x 3.1cm
●	VCC: 3.3-5V
●	GND: The Ground
●	I/O: I/O Interface of SCM

## Experiments and Results

The team used all the sensors and other items to build a system, including DHT11 Humidity and temperature sensor, the buzzer, a fan, a glass box (acts as a vehicle), a bag of ice (mimic cold weather outside), and other necessary objects. Besides, assuming threshold temperature and humidity are 20℃ and 55% (the buzzer will ring at this condition), respectively. When a driver enters a car and breaths after several minutes, the inside humidity will increase. The temperature of the inner side of the windshield will decrease because of the cold weather (acted by the bag of ice).

### Experiment Steps

1.	Connect humidity and temperature sensor and buzzer to the circuit board and make sure the experiment system is in charge. 

2.	Stick DHT11 Humidity and temperature sensor to the bottom side of the box, whose function likes the windshield of vehicles. This sensor measures the temperature and humidity of the inner side of the bottom. Keep this system in a stable environment (focusing on temperature and humidity) for a while. (The original environment is warm and try, with the temperature of 25℃ and humidity of 35%)

3.	Put the bag of ice to the aiming side of the glass box, exhale to the box one time, then close the box and see how temperature and humidity data changed as time goes by. (Reminder: this experiment aims to research on a cold, wet day)

4.	Check the usefulness of Python code and the working conditions of system components. 

### Experiment Results

1.	When temperature and humidity reach 20℃ and 55%, respectively. A notice called “Fog Alarm!” appeared on the screen and three times of buzzer ringing means defog. 

2.	After three times of ringing, the fan starts to work and blow away the fog for about one minute, then the humidity decreases to under 55%. According to designated conditions, buzzer and fan stopped working when one of the thresholds cannot be satisfied. 

3.	When both thresholds were reached again, the buzzer and fan would start working again.

### Experiment Code

The experiment code below shows how a computer controls the experiment system’s actions. It seems that the computer sends demands to system components when to work or finish working.

## Discussion

The foggy windshield, which blocks drivers’ vision, may lead to traffic safety concerns. Based on the psychrometer chart, water vapor is more likely to condensate under low temperatures. Therefore, this safety problem is more serious for vehicles in cold areas, such as New York City and Pittsburgh. Our Waking-up System for Rear Window Defogger is designed to detect the fog formation on the rear window and clean it automatically as well as alerting the driver. Our group builds the system with a fan, a buzzer, and a temperature and humidity sensor. The experiment is carried on at room temperature but the ice bag is applied to simulate windows under the cold weather. Adding water vapor into the box with room temperature does not guarantee the formation of fog. However, after the glass box contacting with the ice bag, fog rapidly forms on the glass wall. Therefore, the temperature is the more deterministic factor in fog formation. After several trials, we find out the threshold is 20-degree Celsius and 55% relative humidity. As glass temperature decreases room temperature below 20-degree Celsius and the relative humidity is larger than 55% relative humidity, the fog is visible on the glass. At this point, the fan is activated to accelerate air circulation and buzzer beeps to alert the driver. 

Some improvements can be made to the accuracy of the sensing and efficiency of defogger. One of the limitations of the sensing system is the low accuracy of the sensor. It has an outer shield separating the sensing component from the glass surface, so it has a lagged effect on detecting the temperature and humidity. The sensor has ±5% accuracy in measuring relative humidity and ±2°C accuracy, which cannot monitor the slight change. Also, the efficiency of defogger can be heightened by adding in the higher power supply. The fan is designed for 12V power supply but we can only apply a 5V power supply, which utilizes a partial power of the fan. Besides from the circuit, the algorithm can be improved by adding another temperature and humidity sensor for the air in the glass box. By the temperature and humidity difference between the air and glass, we can predict the fog formation in a wider temperature range. If the project could be implemented, we can test the system in a real vehicle instead of the glass box. 


## References

[1] Engineering Toolbox. Psychrometric chart. Retrieved from: https://www.engineeringtoolbox.com

[2] Adafruit Industries. “DHT11 Basic Temperature-Humidity Sensor + Extras.” Adafruit Industries Blog RSS. Retrieved from:  www.adafruit.com/product/386.

[3] Amber. (2018, Nov 16)“Search Archive:dht11. Retrieved from: Kookyecom, kookye.com/?s=dht11.

[4] Tarun Agarwal. (2019) Temperature Sensors – Types, Working & Operation. Retrieved from:
https://www.elprocus.com/temperature-sensors-types-working-operation/

[5] “GP.” ( 2010) Amazon, Goettsche Partners. Retrieved from: https://www.amazon.com/gp/product/B00KF7MVI2/ref=ppx_yo_dt_b_asin_title_o02_s02?ie=UTF8&psc=1.
