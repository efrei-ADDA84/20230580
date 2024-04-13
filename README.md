# TP2 Devops : Meteo Checker App And auto-deployement on docker

The Meteo Checker App allows you to retrieve weather information using latitude and longitude coordinates via the OpenWeather API.


## Lab Aims

* We should use the app like and API
* **Run** the app docker images with ```docker run -p 8080:8080 --env API_KEY="YOUR API KEY" noebrt/meteo_checker```
* **Request** our app with a **CURL query** : ```curl "http://localhost:8080/?lat=48.75722028315804&lon=2.3261414356815058"```
* Automate the build and the push of a docker images after each push with a **Github Action Workflow**

## Languages Used

JavaScript (Node JS alpine3.19)

## Dependencies 

* Npm 10.5.2
* openssl 3.1.4-r6
* tar 1.35-r2
* dotenv 16.4.5 (Usage of env variable)
* express 4.19.2 (Creation of the API)

The choice of version is related to their lack of vulnerabilities.

## Security 

0 Vulnerabilities detected on Trivy or Docker Scout

### Trivy 

```sudo docker run --rm -v /var/run/docker.sock:/var/run/docker.sock aquasec/trivy:0.18.3 noebrt/meteo_checker```
![Uploading Capture d’écran 2024-04-13 à 21.20.28.png…]()



### Docker
You can pull the Docker image with the following command:
```
docker pull noebrt/meteo_checker:latest
```



## How To Use 

To use the Meteo Checker App, follow these steps:

1. Make sure you have Docker installed on your system.

2. Run the Docker container with the following command, replacing the placeholders with your actual latitude, longitude, and OpenWeather API key:
```
docker run --env LAT="Your Latitude" --env LON="Your Longitude" --env API_KEY="Your OpenWeather API Key" noebrt/meteo_checker:latest
```
## API Key 
Obtain an API key by signing up on the OpenWeather website [here](https://openweathermap.org/api).

## Example Queries

Here are some example queries you can use with the Meteo Checker App:

- Retrieve current weather for Villejuif:
  ```
  docker run --env LAT="48.7887654119804" --env LON="2.3638803269592468" --env API_KEY="Your API Key" noebrt/meteo_checker:latest
  ```

- Get weather for Tours:
  ```
  docker run --env LAT="47.39563393240081" --env LON="0.6901326836654383" --env API_KEY="Your API Key" noebrt/meteo_checker:latest
  ```

## Example Response
https://github.com/efrei-ADDA84/20230580
  ```
  docker run --env LAT="48.7887654119804" --env LON="2.3638803269592468" --env API_KEY="Your API Key" noebrt/meteo_checker:latest
  ```
Response :

```
{
  coord: { lon: 2.3639, lat: 48.7888 },
  weather: [
    {
      id: 803,
      main: 'Clouds',
      description: 'broken clouds',
      icon: '04d'
    }
  ],
  base: 'stations',
  main: {
    temp: 10.28,
    feels_like: 9.45,
    temp_min: 9.26,
    temp_max: 11.95,
    pressure: 997,
    humidity: 80
  },
  visibility: 10000,
  wind: { speed: 3.09, deg: 160 },
  clouds: { all: 75 },
  dt: 1711805837,
  sys: {
    type: 1,
    id: 6548,
    country: 'FR',
    sunrise: 1711776701,
    sunset: 1711822671
  },
  timezone: 3600,
  id: 2968705,
  name: 'Villejuif',
  cod: 200
}
```
Feel free to explore more queries based on your needs and geographic locations!

## Technical choise 
* Wrapper : Node JS
  - JavaScript is one of the most pratical language to manage json api, especially with axios
* Container : Docker
  - Docker is the most used container technologies


Lack of vulnerabilities

For patch tar 6.2.1 I install the new patch npm install -g npm@10.5.2



