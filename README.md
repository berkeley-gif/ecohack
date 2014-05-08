Cal-Adapt Resources for EcoHack SF 2014
====================

We are in the midst of developing a RESTful API for Cal-Adapt, but in the meantime you can access some of the California climate data through these urls.

Local Climate Snapshots
---------------------
Given a lat/long you'll be able to get the data values that populate the charts for Temperature, Fire, Snowpack. To see the tool in action check out http://cal-adapt.org/tools/factsheet/

### Temperature
Projected change in annual average temperatures across California under a low carbon emissions scenario (B1).

URL

```
http://cal-adapt.org/data/baseline/tair/?scenario=a2&lng=-121.4703369140625&lat=38.56964280859043&factsheet=true&county=false&units=imperial
```

Response

```json
{"h": 61.609999999999999, "a2": 67.870000000000005, "b1": 65.189999999999998}
```

### Snow
Projected changes in April snow water equivalence (SNWE) across California under a low carbon emissions scenario (B1) and a high carbon emissions scenario (A2). The baseline time period is 1961-1990 and the end of century time period is 2070-2090.

URL

```
http://cal-adapt.org/data/baseline/snwe/?scenario=a2&lng=-123.20068359375&lat=40.36328834091582&factsheet=true&county=true&units=imperial&month=4
```

Response

```json
{ 
  "a2" : { 
      "baseline" : 3.2799999999999998,
      "century_end" : 0.44,
      "data" : [ 
	  0.37,
          0.0,
          0.76000000000000001,
          0.66000000000000003,
          0.45000000000000001,
          0.0,
          1.1000000000000001,
          1.49,
          0.28999999999999998,
          0.54000000000000004,
          1.1299999999999999,
          0.35999999999999999,
          0.11,
          0.0,
          0.98999999999999999,
          0.14999999999999999,
          0.45000000000000001,
          1.8799999999999999,
          0.62,
          0.19,
          0.0,
          0.0,
          0.0,
          0.93000000000000005,
          0.0,
          0.17000000000000001,
          0.0,
          0.0,
          0.17000000000000001,
          0.32000000000000001
        ],
      "pct_change" : -86.700000000000003
    },
  "b1" : {
      "baseline" : 3.1400000000000001,
      "century_end" : 0.95999999999999996,
      "data" : [ 
          1.5800000000000001,
          1.3300000000000001,
          0.17000000000000001,
          0.0,
          1.3,
          0.0,
          0.10000000000000001,
          0.40000000000000002,
          2.3900000000000001,
          3.0,
          0.90000000000000002,
          0.83999999999999997,
          2.5299999999999998,
          0.69999999999999996,
          0.0,
          0.0,
          0.12,
          0.20999999999999999,
          1.22,
          1.3799999999999999,
          0.11,
          0.82999999999999996,
          0.54000000000000004,
          1.8,
          2.3500000000000001,
          2.2400000000000002,
          0.0,
          0.87,
          0.66000000000000003,
          1.26
        ],
      "pct_change" : -69.400000000000006
    }
}
```

### Wildfire
Projected increase in potential amount of area burned in 2085, as compared to present risk, across California under a low carbon emissions scenario (B1) and a high carbon emissions scenario (A2) for the CNRM model. The data are projected values for years 2020, 2050 and 2085.

URL

```
http://cal-adapt.org/data/baseline/fire/?scenario=a2&lng=-122.6348876953125&lat=38.81831117374662&factsheet=true&county=true&units=imperial
```

Response

```javascript
{ 
  "a2" : { 
      "baseline" : 1.3700000000000001,
      "century_end" : 1.3700000000000001,
      "data" : [
          1.1899999999999999,
          1.28,
          1.6399999999999999
        ],
      "pct_change" : 0.0
    },
  "b1" : { 
      "baseline" : 1.24,
      "century_end" : 1.24,
      "data" : [ 
          1.1599999999999999,
          1.27,
          1.3100000000000001
        ],
      "pct_change" : 0.0
    }
}
```






Extreme Heat Tool:
---------------------
Given a lat/long you'll be able to get an annual count of the number of days projected to cross the given extreme heat threshold for that location from 1950-2099. To see the tool in action check out http://cal-adapt.org/temperature/heat/

URL

```
http://cal-adapt.org/temperature/heat_days.json/?tq=lng%3D-123.20068359375%26lat%3D40.12849105685408%26scenario%3Da2%26model%3Dgfdl%26type%3Dnumdays%26units%3Dimperial%26climvar%3Dtmax&tqx=reqId%3A0
```

Response

The url returns a Google Charts API JSONP object as response.  

```javascript
google.visualization.Query.setResponse({'version':'0.6', 'reqId':'0', 'status':'OK', 'table': {cols:[{id:'Year',label:'Year',type:'date'},{id:'Number of Extreme Heat Days',label:'Number of Extreme Heat Days',type:'number',p:{'climnorm_avg_numdays':'4.3','extreme_heat_threshold':'91.7189984131'}}],rows:[{c:[{v:new Date(1950,0,1)},{v:10}]},........{c:[{v:new Date(2099,0,1)},{v:35}]}]}});
```

A quick [gist](https://gist.github.com/mukhtyar/e54bf08a1ef5ffeb2933) to help you get started working with a Google Charts API JSONP object.