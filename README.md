### Team Members

Yaxian Zheng, Cheng Zhang, Kaiwen Zhang, Yanbo Zhang

## Introduction
 
The Waking-up System for Rear Window Defogger is an automated anti-fog system. This system combines the fog detection, automatic activation of defogger and driver notice properties. The fog detection property is achieved by gathering air temperature in the vehicle and the temperature and humidity of rear window glass. The system can predict the formation of fog and activate the fan at the rear window and beep the buzzer once to alert the driver. The fan would stop as the rear window is cleared. Furthermore, the users can monitor the temperature and humidity change in their vehicles during a period on the website “OpenChirp”. 

### Motivation

Vehicle windshield fogging is considered as a potential safety problem. The presence of fog on the windshield blurs the window and blocks drivers’ vision. Especially in areas with cold winters, drivers are more likely to turn on the heaters, which result in fog on the inside of windows. A defogger plays an important role in clearing up the fogged windshield by blowing out warm air. Normally, the front window defogger is activated by drivers manually, as they noticed the formation of fog. However, the drivers rarely could notice the formation of fog on the rear window on time, because they pay more attention to the front. When deciding to make a turn or back up, they just realize the fog on the rear window. With blocked backward sight, accidents are likely to happen. 

The extreme cold and snowy winter in Pittsburgh cause more driving safety concerns than the warm area. Therefore, the Waking-up System for Rear Window Defogger can play a more crucial and practical role for traffic accident prevention.  

### Goals
The goal of this project is to justify the accessibility of fog prediction and the automatic defogger in the system. The whole system is installed and tested inside a glass box. The final project can detect the fog on the glass wall by gathering the air temperature and relative humidity and temperature on the glass. The automatic defogger can activate and stop as the numerical data reaches the threshold. Furthermore, the buzzer is capable to beep one time and stop as the numerical data overcomes the threshold. If the sensitivity and predictive capacity increase, the project may be able to apply to real vehicles. 

## Methodology

In order to defog on the rear window inner surface, the physical principles of fogging and methods to defog are explained. The sensors used to detect fog generation and signal processing are analysed in this part.

### Phenomena of Interest

#### Physical Principles

The generation of fog on a surface usually can be contributed to the fact that the temperature of this surface has reached the dew point temperature of its surrounding air. The water vapor in the surrounding air consequently will condense on this surface. The cause for this phenomenon is that the surface temperature is largely lower than the surrounding temperature due to some specific reasons. For example, small dew point can be seen generating on the beneath surface of grass in the morning. This is largely because the cold ground continuously radiates to the beneath surface which results in the condensation of the surrounding air of grass. In the car window case, the humidity ratio in car is usually at a high level since the breathing effects of humans. When the inner surface of car window has a temperature lower than the dew point temperature of its surrounding air due to cold outside weather, fogging will occur on the inner surface. 

The methods of defogging usually are out of two principles. One of them is to decrease the water vapor content around the window. This can be accomplished by blowing cold air into the car since the cooling system in cars usually 	are combined with the function of drying air. 

### Sensors Used

DHT11 sensor is used to detect the generation of fog. It has 3 pin and sends its temperature and relative humidity data to Raspberry Pi. Its technical details are shown as following:

#### DHT11 Humidity and temperature sensor 

· Low cost

· 3 to 5V power and I/O

· 2.5mA max current use during conversion (while requesting data)

· Good for 20-80% humidity readings with 5% accuracy

· Good for 0-50°C temperature readings ±2°C accuracy

· No more than 1 Hz sampling rate (once every second)

· Body size 15.5mm x 12mm x 5.5mm

· 4 pins with 0.1" spacing

The DHT11 detects water vapor by measuring the electrical resistance between two electrodes (Amber). Between the electrodes, a moisture holding substrate can absorb water vapor. The substrate releases free ions, which increases the conductivity between the electrode, as water vapor enters it. The humidity sensing component is a moisture holding substrate with electrodes applied to the surface. When water vapor is absorbed by the substrate, ions are released by the substrate which increases the conductivity between the electrodes. The change in resistance between the two electrodes is proportional to the relative humidity. Higher relative humidity decreases the resistance between the electrodes, while lower relative humidity increases the resistance between the electrodes [humi].

The DHT11 measures temperature with a surface mounted NTC temperature sensor (thermistor) built into the unit.

With the plastic housing removed, you can see the electrodes applied to the substrate, an IC mounted on the back of the unit converts the resistance measurement to relative humidity. It also stores the calibration coefficients, and controls the data signal transmission between the DHT11 and the Arduino:

![sensor](https://user-images.githubusercontent.com/42809684/66973309-9c878100-f065-11e9-99c5-bf38f289d4d6.png)

<p align="center">Figure 2. Picture of DHT11<sup>[1]</sup></p>

<div align=center><img width="150" height="150" src="http://img.blog.csdn.net/20161028230559575"/></div>


We use Noctua NF-R8 redux-1800 PWM cooling fan to react with the humidity increase and defog the window. This cooling fan is a 4-pin fan with the voltage of 12V. Its detailed characteristics are listed as below:


### Signal Conditioning and Processing

Describe the signal conditioning and processing procedures

## Experiments and Results

Describe the experiments you did and present the results; Use tables and plots if possible

## Discussion

Discuss the insights from the project

## References

[1] Amber. (2018, Nov 16)“Search Archive:dht11. Retrieved from: Kookyecom, kookye.com/?s=dht11.

[2] Tarun Agarwal. (2019) Temperature Sensors – Types, Working & Operation. Retrieved from:
https://www.elprocus.com/temperature-sensors-types-working-operation/

[3] “GP.” ( 2010) Amazon, Goettsche Partners. Retrieved from: https://www.amazon.com/gp/product/B00KF7MVI2/ref=ppx_yo_dt_b_asin_title_o02_s02?ie=UTF8&psc=1.
