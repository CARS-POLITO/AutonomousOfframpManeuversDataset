# Autonomous Off-ramp Maneuvers Dataset


This repository contains the dataset and a description of the data used in [Estimation of passenger comfort level for autonomous highway off-ramp maneuvers](https://link.to.paper).
This experimental dataset is composed of ***78 off-ramp exit maneuvers*** traveled along the Norwegian highways. Data are gathered on a Battery Electric Vehicle (BEV) featured with L2+ driving automation functions. This study is conducted in a real-world environment, with the use of specific testing equipment. Data are acquired in the surroundings of Oslo, Bergen, Stavanger and Kristiansand.

This dataset is used for assessing the level of comfort associated with autonomous highway off-ramp maneuvers. As a consequence, each tested highway exit had to be carried out under **two different operating conditions** - **driving manually** for calibration purposes and **driving under vehicle autonomous control action**, called **AD-SW (AutonomousDriving-Software)** mode. 

![exterimental_test_location](docs/vehicledata.png)  
Example of logged vehicle speed, longitudinal and lateral acceleration along the highway off-ramp exit no. 44 Gjelleråsen/Nittedal/Hellerudsletta on E6.

![vehicle_view](docs/view_vehicle.png)

Scene view camera output recorded during experimental tests.

## Dataset
Please follow this [link](https://www.cars.polito.it/research/research_data) to download the dataset (~5MB).

## Dataset structure
The dataset contains one folder, called **Maneuvers**, that includes all the tested maneuvers, and a **Matlab script file** used to visualize the selected data (*Data_setup.m*). The **Maneuvers** folder comprises 78 subdirectories called ***data_yearmonthdayThourminutesecond***. Each folder contains the associated *.mat*, *.xls* and *.csv* files with the measured signals logged during experimental testing (***signals_yearmonthdayThourminutesecond***). Below is the structure of an experimental maneuver as an example.

```
Maneuvers
├── data_yearmonthdayThourminutesecond
│   ├── signals_yearmonthdayThourminutesecond
│   │   │── Time_s.. (Time recorder [s])
│   │   │── VehSpd_kph.. (Vehicle speed [kmh^{-1}])
│   │   │── LgtA_mpss.. (Longitudinal acceleration [ms^{-2}])
│   │   │── LatA_mpss.. (Lateral acceleration [ms^{-2}])
│   │   │── DA_status_.. (Driver assistance status [-], 1 active, 0 idle)
│   │   │── Right_turn_indic_.. (Right turn indicator [-], 1 active, 0 idle)
│   │   │── GPS_lat_deg.. (GPS Latitude vehicle position [deg])
│   │   │── GPS_lon_deg.. (GPS Longitude vehicle position [deg])
│   │   │── GPS_timestamp_.. (GPS Time stamp [s])
│   │   │── Curvature_m-1.. (Road Curvature estimation [m^{-1}])
```
To distinguish autonomous maneuvers from manual ones, it will be necessary to verify that signal *DA_status_* is 1, which means active.


## Data description
Please check our paper for a detailed data description. The following provides a brief summary.

### Signals Recording
Given the extended duration of each test, it becomes imperative to employ a methodology for extracting pertinent timestamps from the data. In our particular study, a tagging approach was implemented to fulfill this requirement. Therefore, when the driver activates the vehicle's right turn indicator, the autonomous control system is triggered to initiate the self-driving off-ramp manoeuvre. Active steering towards the highway deceleration ramp is triggered by the right turn indicator. This is when manoeuvre data logging commences. Rather, the manoeuvre data logging ends when the *DA enable status* falls to 0. Thus, the active guidance is disabled and the driver takes full control of the vehicle.

![Tagging procedure](docs/taggingprocedure.png)

Example of signal data recording based on driver right turn indicator activation and autonomous controller deceleration request.

## Citation
If you find our work useful in your research or use any part of the data provided in this repository, please cite it as:
> Eugenio Tramacere, Luis Castellanos, Sara Luciani, Paolo Urgesi, Nicola Amati (202x). Estimation of passenger comfort level for autonomous highway off-ramp maneuvers.

    @ARTICLE{--,
  	    author={Tramacere, Eugenio and Castellonos, Luis and Luciani, Sara and Urgesi, Paolo and Amati, Nicola},
  	    journal={-}, 
  	    title={Estimation of passenger comfort level for autonomous highway off-ramp maneuvers}, 
  	    year={202x},
  	    volume={},
  	    number={},
  	    pages={-},
  	    doi={-}}
## License
All data data are made available under a [CC 4.0 license](http://creativecommons.org/licenses/by/4.0). You can freely use this dataset, so long as you provide attribution to the authors.
The manuscript text is not open source. The authors reserve the rights to the article content, which is currently submitted for publication in *Applied Ergonomics, Elsevier*.

## Acknowledgments
The present research has been developed as a result of the cooperation between [CARS, Politecnico di Torino](https://www.cars.polito.it/) and [NIO](https://www.nio.com/). Special thanks to *Eng. Paolo Urgesi* who made this fruitful collaboration possible.
