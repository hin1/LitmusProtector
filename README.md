# LitmusProtector
A network of devices to galvanise a new wave of Community First Responders (CFR).
Presented by Team LitFam (Lum Wei Boon , Sean Chan, Yap Zuo Ming, Sing Hui, Peh Zhi Qian Justin)

## A short description of the problem you are tackling, how technology can help, as well as the idea your team is proposing*
## Pitch Video
## Architecture and Details
## Getting started
1. Import [network-flows.json](./network-flows.json) into a Node-RED application on IBM Cloud.
2. Sign up for [Twilio API's](https://www.twilio.com) SMS service to generate a new number to send messages from.
3. After connecting up a Raspberry Pi connected wirelessly to a IoT Smoke Sensor to an instance of the IBM Watson IoT Platform, import [device-flows.json](./device-flows.json) on a Node-RED application on the Pi.

## Demo
Visit our Node-RED [website](https://detector-network.mybluemix.net/svgtest/) to take a look at an example of the dashboard of the application showing
households on fire or not. 

## What LitFam used to build LitmusProtector

* IBM Cloudant - Deploy the Node-RED applications
* IBM Cloud Node-RED- Organise the flows of both the network and the sensor data sent by the devices
* IBM Watson IoT Platform - To handle sensor data from multiple devices
* IBM Cloud Visual Recognition Service - To process images sent by the device and detect for fire