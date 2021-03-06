![logo](./resources/logo.jpeg)
# LitmusProtector
A network of devices to galvanise a new wave of Community First Responders (CFR).
Presented by Team Litmus Xmas (Lum Wei Boon, Sean Chan, Yap Zuo Ming, Sing Hui, Peh Zhi Qian Justin)

## Introduction
Residential fires made up more than 40% of all fire calls made to the SCDF in 2019. Many of those are unattended cooking, and can be put out by community first responders if detected early. Our device seeks to address this issue, and also foster a sense of community spirit when neighbours help one another out.

The Litmus Protector is a smart smoke detector with a camera and connection to the internet. When the smoke alarm is activated, the feed from the camera will be streamed to the residents' mobile devices. The user can send a distress signal instantly to neighbours in the same block for help. A system override will also occur after a set duration that will send a distress signal to neighbours.

## Pitch Video
[Watch our pitch video here!](https://youtu.be/RYOL_69DhzA)

## Architecture and Details
![Architecture](./resources/Architecture.png)
Figure 1

Litmus Protector consists two main parts. The first is the actual Litmus Protector device, which is a smart home fire and smoke detector using a PiCamera and a Xiaomi Mijia Honeywell Smoke Detector based on a Raspberry Pi. The second part would be the IoT network hosted on IBM Cloud, which monitors individual Litmus Protector devices and sends distress signals to the neighbours' phones.

![Device Flow](./resources/DeviceFlow.png)
Figure 2
![Server Flow](./resources/ServerFlow.png)
Figure 3

Figure 2 and 3 shows the flow node-RED flow diagrams for the devices and server side code respectively

On the device side, the smoke detector will periodically send status updates to our Raspberry Pi. We will then check if the status is that of a smoke detection. If so, we will inform the cloud server and also capture a photo of the kitchen and send it to the server for processing.

On the server side, there are 3 key components: 1) Dashboard rendering 2) AI fire processing 3) Distress Notification.
Dashboard rendering shows a live illustration of the status of the homes in a HDB. It is built with Vue.JS on top of node-RED's dashboard flow. Fire-image processing is done using IBM's visual recognition service. Lastly the distress and alert notifications are implemented using the Twillio API's.

Additionally, we are currently lacking the mobile device functionalities such as turning off the alarm, and manually triggering the distress signal.

![demo1](./resources/demo1.jpeg)
![demo2](./resources/demo2.jpeg)
The above 2 images demonstrates how our device can be set-up in the kitchen. Essentailly the webcam and Raspberry pi must be connected, but the smoke-detector has a wireless LAN connection with the Pi.

## Getting started
1. Import [network-flows.json](./network-flows.json) into a Node-RED application on IBM Cloud.
2. Sign up for [Twilio API's](https://www.twilio.com) SMS service to generate a new number to send messages from.
3. After connecting up a Raspberry Pi connected wirelessly to a IoT Smoke Sensor to an instance of the IBM Watson IoT Platform, import [device-flows.json](./device-flows.json) on a Node-RED application on the Pi.

## Demo
Visit our Node-RED [website](https://detector-network.mybluemix.net/svgtest/) to take a look at an example of the dashboard of the application showing
households on fire or not. 

## Hardware Required
![hardware](./resources/hardware.jpeg)

* Raspberry Pi (with Raspbian installed)
* Xiaomi Smoke Detector
* Xiaomi Smart home hub
* USB Webcam / PiCamera

## Software used to build LitmusProtector

* IBM Cloudant - Deploy the Node-RED applications
* IBM Cloud Node-RED- Organise the flows of both the network and the sensor data sent by the devices
* IBM Watson IoT Platform - To handle sensor data from multiple devices
* IBM Cloud Visual Recognition Service - To process images sent by the device and detect for fire
* Twillio API
* Raspbian
* Zigbee (Xiaomi-Smart Home)

## Future enhancements 
* Development of mobile application (statistics, distress signalling, etc.)