# RoboticBase example: UoA PoC 2

An unmaned delivery proof of concept by using multiple autonomous mobile robots connected to RoboticBase.

This PoC is based of [RoboticBase version 0.4.4](https://github.com/RoboticBase/core/releases/tag/0.4.4) and [FIWARE Release 7.7.1](https://github.com/FIWARE/catalogue/releases/tag/FIWARE_7.7.1).

## Description
"RoboticBase" is a robot management platform based on [FIWARE](http://www.fiware.org/) which enables you to manage and operate many kinds of robots and IoT devices as interactions of contexts.

"RoboticBase" allows robots to collaborate with IoT devices, Open Data, human beings and so on. You can connect a robot to "RoboticBase" using the open APIs of the robot, and operate the robot through those APIs. In turn, "RoboticBase" has an ability to manage ROS. If you connect a ROS robot to "RoboticBase", you can operate the robot directly without restrictions.  
For example, you can deploy a ROS program to the robot and access the raw data of the robot through "RoboticBase".


![architecture.png](/docs/images/architecture.png)

## components
|platform|summary|version|
|:--|:--|:--|
|[kubernetes](https://kubernetes.io/)|Container Orchestration Platform|1.14 or higher|
|[robot-controller](https://github.com/RoboticBase/uoa-poc2-controller)|Waypoint management, Global route planning, Robot action handling, ...|0.1.0|
|[robot-ui](https://github.com/RoboticBase/uoa-poc2-robotui)|User interface of mobile robots|0.1.0|
|[ordering](https://github.com/RoboticBase/zaico-extensions)|Ordering service using cloud inventory control service|0.1.0|
|[FIWARE orion](https://fiware-orion.readthedocs.io/en/master/)|Publish/Subscribe Context Broker|2.2.0|
|[FIWARE cygnus](https://fiware-cygnus.readthedocs.io/en/latest/)|Data collection and Persistence Agent|1.15.0|
|[FIWARE sth-comet](https://fiware-sth-comet.readthedocs.io/en/latest/)|An Agent to manage historical raw and aggregated time series context|2.5.0|
|[FIWARE iotagent-json](https://fiware-iotagent-json.readthedocs.io/en/latest/)|Backend Device Management Agent|1.10.0||
|[ambassador](https://www.getambassador.io/)|API Gateway|0.73.0|
|[auth](https://github.com/RoboticBase/fiware-ambassador-auth)|Authorization and Authentication component working with ambassador|0.3.0|
|[RabbitMQ](https://www.rabbitmq.com/)|Distributed Message Queue|3.7.16|
|[MongoDB](https://www.mongodb.com/)|Document-oriented NoSQL Database|4.1.13|

|autonomous mobile robots|summary|version|
|:--|:--|:--|
|[bridge](https://github.com/RoboticBase/uoa_poc2_bridge)|ROS package for bridging autonomous mobile robots and FIWARE|0.1.0|
|[ROS](https://www.ros.org/)|A set of software libraries and tools to build robot applications|Kinetic Kame|
|[Navigation Stack](http://wiki.ros.org/navigation)|2D mobile robot navigation using AMCL and LOAM||


## An experiment to prove our concept
We and University of Aizu have been performed an unmaned delivery experiment on Nov. 26th - 29th , 2019.

Please see below movies:

* short version (4min 5sec)
[![short version](https://img.youtube.com/vi/R09vPSEbg1g/0.jpg)](https://www.youtube.com/watch?v=R09vPSEbg1g)

* long version (10min 33sec)
[![long version](https://img.youtube.com/vi/pR10cp93KX4/0.jpg)](https://www.youtube.com/watch?v=pR10cp93KX4)

## Requirements

* kubernetes client PC
    * `azure cli` is required when you use Azure AKS.

||version|
|:--|:--|
|OS|macOS Mojave 10.14.6 or Ubuntu 16.04|
|azure cli|2.0.63|
|kubectl|1.14.1|
|helm|2.13.1|

* Azure AKS

||version|
|:--|:--|
|region|japaneast|
|kubernetes|1.14.6|

## getting started
1. deploy [RoboticBase-core](https://github.com/RoboticBase/core) v0.4.4

1. install python3

1. install jupyter notebook

    ```bash
    $ cd docs/en-jupyter_notebook/
    $ ./setup_jupyter_notebook.sh
    ```
1. start jupyter notebook

    ```bash
    $ ./start_jupyter_notebook.sh
    ```

1. execute the commands in order according to the following documents:
    1. start business logics -- [01\_start\_pods.ipynb](/docs/en-jupyter_notebook/azure_aks/01_start_pods.ipynb).
    1. register mobile robot & ui device to FIWARE  -- [02\_register\_device.ipynb](/docs/en-jupyter_notebook/azure_aks/02_register_device.ipynb).
    1. register business logic and master data to FIWARE -- [03\_register\_business\_logic.ipynb](/docs/en-jupyter_notebook/azure_aks/03_register_business_logic.ipynb).
    1. initialize FIWARE entities -- [04\_initialize.ipynb](/docs/en-jupyter_notebook/azure_aks/04_initialize.ipynb).
    1. simulate a scenario to confirm that the platform started correctly -- [05\_simulate\_scenario.ipynb](/docs/en-jupyter_notebook/azure_aks/05_simulate_scenario.ipynb).

## License

[Apache License 2.0](/LICENSE)

## Copyright
Copyright (c) 2019 [TIS Inc.](https://www.tis.co.jp/)
