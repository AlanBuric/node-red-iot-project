# Node-RED Internet of Things project

This is an Internet of Things college class project consisting of three separate Node-RED flow examples: a weather station, a smart home and a time clock system.

## Flows and how to reuse them

Most examples have environment variables that need to be configured by double-clicking the flow tab and going to the Environment Variables tab switchable on the right side of the flow's settings. The `*_DATA_PATH` environment variables can be substituted with absolute file paths on your computer. All flows depend on and use [Node-RED Dashboard](https://flows.nodered.org/node/node-red-dashboard).

A flow can be imported and used by copying its JSON file or its contents and pasting it into the Import menu in Node-RED, and configure the environment variables if needed.

### Weather station

![Preview screenshot of Node-RED groups of nodes for the weather station](/screenshots/weather-station.png)
![Preview screenshot of the Node-RED weather station Dashboard with three tabs with inputs, buttons, graphs, gauges and text.](/screenshots/weather-station-dashboard.png)

- **Description:** Fetches the weather parameters of a configured location every 5 minutes from [WeatherAPI.com](https://www.weatherapi.com/) [Realtime API](https://www.weatherapi.com/docs/#apis-realtime) and displays the data in the [Node-RED Dashboard](https://flows.nodered.org/node/node-red-dashboard). The graph data is automatically saved, and loaded upon startup. Miscellaneous data is also displayed and most values are configurable, such as the unit system (imperial and metric), location and temperature extremes.
- **Environment variables:** `TEMPERATURE_GRAPH_DATA_PATH`, `PRESSURE_GRAPH_DATA_PATH`, `WIND_SPEED_GRAPH_DATA_PATH`, `WEATHERAPI_KEY`

### Time clock system

![Preview screenshot of Node-RED groups of nodes for the time clock system: an office group on the left side consisting of an Internet of Things Gateway and and three devices with user interfaces, all connected to the gateway, which connects to a cloud service group on the right side](/screenshots/time-clock-system.png)
![Preview screenshot of the Node-RED time clock system Dashboard: three user interfaces and three administration interfaces. The user interfaces each have an organization user ID input, while the administration interfaces a user ID removal and new user ID adding input.](/screenshots/time-clock-system-dashboard.png)

- **Description:** Enables registered user IDs to register their office entrance moment and then their exit moment by their employee ID (e.g. via RFID) onto any of the three devices at the company's office. Administration panel in [Node-RED Dashboard](https://flows.nodered.org/node/node-red-dashboard) enables the adding and removal of user IDs. Communication is performed via the Internet of Things Gateway and to the Cloud IoT controller which sends an appropriate response to device which generated the response, which is literally a simulation of the HTTP REST API. Employee IDs and their time data are loaded and stored in a JSON file.
- **Environment variables:** `COMPANY_EMPLOYEES_DATA_PATH`

### Smart home

![Preview screenshot of Node-RED groups of nodes for the smart home: a central Internet of Things Gateway, Inject nodes simulating the sensors and the Node-RED Dashboard inputs on the right side](/screenshots/smart-home.png)
![Preview screenshot of the Node-RED smart home Dashboard with input switches for locks and numbers for outdoor light duration.](/screenshots/smart-home-dashboard.png)

- **Description:** Three sensors communicate with the Internet of Things Gateway, which performs all the logic and also communicates with the [Node-RED Dashboard](https://flows.nodered.org/node/node-red-dashboard). A garage motion sensor triggers a camera to AI detect the owner's registration plate while the owner is driving towards the garage, and opens the garage door if there's a match. A front door lock sensor signal will trigger the Gateway to close the garage door if it's already open and the front door is being locked. An outdoor motion sensor turns on the outdoor lights if motion is detected at night, and turns off in 5 seconds by default. All "things" are controllable via the Dashboard as well.
- **Environment variables:** none.