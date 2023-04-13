# IoT environment system

> IoT-based environmental monitoring system that tracks temperature and humidity levels in real-time through sensors and presents the data through an intuitive, visual dashboard.

## Features

- Real-time Monitoring: Monitors temperature and humidity levels in real-time using DHT11 digital sensors connected to a Raspberry Pi.
- Visual Dashboard: Presents real-time data through an easy-to-use visual dashboard built with Apache Echarts, allowing users to easily track environmental changes and trends. Users can view data in different time intervals.
- User Management: Supports multiple users with different roles, including administrators and normal users, to restrict authorization of actions based on user permissions.
- Sensor Management: Enables users to add and delete sensors from the application, allowing for greater flexibility in monitoring different environments.
- Cloud-based Storage: Stores data securely in the cloud using AWS IoT Core and RDS, ensuring that data is protected and always accessible. Additionally, the system uses VPC and EC2 to provide a secure and scalable infrastructure for the web application.

## Tech Stack

- 💻 Raspberry Pi: Small, low-cost computer used as an IoT device to collect data from the DHT11 sensor.
- 🌡️ DHT11: Digital sensor that measures temperature and humidity.
- 📡 MQTT: Lightweight messaging protocol that enables the Raspberry Pi to publish sensor data to the AWS IoT Core in real-time.
- 🐍 Python: High-level programming language used for both the Raspberry Pi and Django server development.
- 🕸️ Django: Web framework for Python.
- ☁️ AWS (IoT Core, Lambda, RDS, VPC, EC2): Cloud computing services used to receive, process, store and analyze data collected from the Raspberry Pi and to host the web application.
- 📈 Apache Echarts: Data visualization library for creating graphs and charts to represent environmental data.
- 🛠️ Django REST Framework: Toolkit for building the RESTful API with Django.
- 🌐 Nginx: Web server used to serve the static files for the web application and to proxy requests to the backend server.

## Cloud Architecture

![cloud-architecture](assets/cloud-architecture.png)

This system involves a cloud architecture that consists of the following components:

- Raspberry Pi: The Raspberry Pi is responsible for collecting data from the DHT11 sensor and transmitting it to the cloud using the MQTT protocol.
- AWS IoT Core: The AWS IoT Core MQTT client is used to receive the data transmitted by the Raspberry Pi and trigger an AWS Lambda function.
- AWS Lambda: The Lambda function is responsible for storing the data into an AWS RDS database. It is triggered by AWS IoT Core whenever new data is received from the Raspberry Pi.
- AWS RDS: The AWS RDS database is hosted within a VPC. It stores the environmental data with timestamps and enables us to retrieve and analyze it as needed.
- Web Application: A web application is developped with Django to provide an interactive interface for managing and visualizing the sensor data. It is deployed on an AWS EC2.
- AWS EC2: The web application is deployed on an AWS EC2 instance, which is configured to run nginx and uwsgi to handle HTTP requests.
- AWS VPC: The AWS VPC is used to host the AWS RDS database and EC2 instance. NAT in the VPC is configured to enable access to the web application from the public network.
- RESTful APIs: With Django REST Framework, RESTful APIs enable functionality such as sensor management. These APIs can be accessed by the Raspberry Pi, enabling it to interact with the system remotely.

## Application interface

![img](assets/page-login.png)

![img](assets/page-dashboard.png)

![img](assets/page-temperature.png)

![img](assets/page-humidity.png)

![img](assets/page-devices.png)

![img](assets/page-add-device.png)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE.md) file for details.