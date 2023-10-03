# Autonomous Off-ramp Maneuvers Dataset


This repository contains the dataset and a description of the data used in [Estimation of passenger comfort level for autonomous highway off-ramp maneuvers](https://link.to.paper).
This experimental dataset is composed of off-ramp exit maneuvers traveled along the Norwegian highways. Data are gathered on a [NIO](https://www.nio.com/) Battery Electric Vehicle (BEV) featured with L2+ driving automation functions. This study is conducted in a real-world environment, with the use of specific testing equipment. Data are acquired in the surroundings of Oslo, Bergen, Stavanger and Kristiansand.

This dataset is used for assessing the level of comfort associated with autonomous highway off-ramp maneuvers. As a consequence, each tested highway exit had to be carried out under **two different operating conditions** - **driving manually** for calibration purposes and **driving under vehicle autonomous control action**, called **AD-SW (AutonomousDriving-Software)** mode. 

![exterimental_test_location](docs/vehicledata.png)  
Example of logged vehicle speed, longitudinal and lateral acceleration along the highway off-ramp exit Salhus/Flaktveit on E16.

![vehicle_view](docs/view_vehicle.png)

Scene view camera output recorded during experimental tests.

## Dataset
Please follow this [link](https://www.cars.polito.it/) to download the dataset (~5MB).

## Dataset structure
The dataset has one folder, called **Maneuvers**, containing all the tested maneuvers, and a **Matlab script file** used to analyze the selected data (*Data_setup.m*). The **Maneuvers** folder contains 82 subdirectories called ***data_yearmonthdayTagxxxxxx***. Each folder contains the associated *.mat* file with the measured signals logged during experimental testing (***signals_yearmonthdayTagxxxxxx***).

```
Maneuvers
├── data_yearmonthdayTagxxxxxx
│   ├── signals_yearmonthdayTagxxxxxx
│   │   │── MeasList_LatA.. (Lateral acceleration signal [gs^{-2}]
│   │   │── MeasList_LgtA.. (Longitudinal acceleration signal [gs^{-2}]
│   │   │── MeasList_VehSpd.. (Vehicle speed signal [kmh^{-1}]
│   │   │── MeasList_GPS_Longitude.. (Longitude position signal [° ' '']
│   │   │── MeasList_GPS_Latitude.. (Latitude position signal [° ' '']
```

## Data description
Please check our paper for a detailed data description. 

### Real dataset
The real dataset was captured during  the [Indy Autonomous Challenge](https://www.indyautonomouschallenge.com/) in Las Vegas in 2022. The vehicle used for data generation was an autonomous AV-21 equipped with three LiDAR sensors, each covering 120° horizontally to cover 360° in total. The .pcd files include the fused point clouds. Labeling was done semi-automatically using the GPS positions of the ego-vehicle and the other vehicles on track. The positions were refined using the point cloud distribution in the proximity of the initially placed 3D bounding boxes. 

### Sim dataset
The sim dataset is distribution-aligned, i.e., scenario-identical, with the real dataset. It was created using Unity and a custom LiDAR sensor model. The environment models the same racetrack as in the real data. The scenarios extracted from the real dataset were replayed in this simulation environment and point clouds were captured using the custom LiDAR sensor model. The labels were generated automatically in Unity.  

![Real AV-21](docs/av21_real.png)![Real AV-21](docs/av21_sim.png)

Real (left) and sim (right) AV21 used for dataset generation


## Citation
If you find our work useful in your research, please consider citing:

    @ARTICLE{Tramacerecomfort,
  	    author={Tramacere, Eugenio and Castellonos, Luis and Luciani, Sara and Urgesi, Paolo and Amati, Nicola},
  	    journal={-}, 
  	    title={Estimation of passenger comfort level for autonomous highway off-ramp maneuvers}, 
  	    year={202x},
  	    volume={},
  	    number={},
  	    pages={-},
  	    doi={-}}
