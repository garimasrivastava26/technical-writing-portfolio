# OpenWeather API

## 1. What the endpoint does 
The endpoint returns current weather conditions and other meteorological data for a specific location.

## 2. HTTP method + endpoint
HTTP method: `GET`


Endpoint: 
```
https://api.openweathermap.org/data/4.0/onecall/current?lat={lat}&lon={lon}&appid={API key}
```


## 3. Required parameters
- `lat`: required – Latitude, decimal (-90; 90)
- `lon`: required – Longitude, decimal (-180; 180)
- `appid`: required – The unique API key

## 4. Optional parameters
- `units`: optional – Units of measurement. standard, metric and imperial units are available. If you do not use the `units` parameter, standard units will be applied by default.
- `lang`: optional - You can use the `lang` parameter to get the output in your language. 

## 5. Authentication
The developer authenticates the request using a unique API key provided through the `appid` parameter.

## 6. Response
The response contains location information and a `data` array. The `data` array contains the current weather information, including temperature, feels-like temperature, and weather conditions.



### 6.1 Response fields
 Field: `temp`  

Path: `response → data[0] → temp`  

Meaning: Current temperature at the requested location.

\
 Field: `feels_like`  

Path: `response → data[0] → feels_like`  

Meaning: The temperature that the weather feels like at the requested location.

\
 Field: `description`  

Path: `response → data [0]→ weather [0]→ description`  
  
Meaning: A short description of the current weather condition.

### 6.2	Error handling
•	400 — Bad Request: This error occurs in any of these scenarios:
1.	A mandatory parameter is missing from the request. 
2.	One or more request parameters have an incorrect format. 
3.	A parameter value is outside the allowed range.

•	401 — Unauthorized: This error occurs if the API key is missing from the request or if the provided API key does not grant access to this API.

•	404 — Not Found: This error occurs if data for the requested parameters, such as `lat` or `lon`, is not available.

•	429 — Too Many Requests: This error occurs if the request quota for the provided API key has been exceeded for this API.

•	5xx — Unexpected Error:  This error occurs when the server encounters an unexpected internal error.

## 7. Request example
```
https://api.openweathermap.org/data/4.0/onecall/current?lat=52.2297&lon=21.0122&units=metric&lang=en&appid={API key}
```


The API request example requests weather for the location at latitude 52.2297 and longitude 21.0122.
The weather data is returned using metric units.
The output is returned in English.

## 8. Response example
```json
{
 	"lat": 51.5,
	"lon": -0.1,
	"timezone": "Europe/London",
	"timezone_offset": 3600,
	"data": [
	      {
		"temp": 13.27,
		"feels_like": 12.15,
		"weather": [
                                 {
			"description": "sky is clear"
		      }	
                           ]
	       }	
              ]
}
```

## 9. Example use case
This API can be used to display weather information on a mobile device's home screen.



















