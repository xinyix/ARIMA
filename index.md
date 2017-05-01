## Introduction


### Generate Data
We first load and print our chosen time series data
```
## load in data
> data(AirPassengers)

## print data
> AirPassengers
     Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec
1949 112 118 132 129 121 135 148 148 136 119 104 118
1950 115 126 141 135 125 149 170 170 158 133 114 140
1951 145 150 178 163 172 178 199 199 184 162 146 166
1952 171 180 193 181 183 218 230 242 209 191 172 194
1953 196 196 236 235 229 243 264 272 237 211 180 201
1954 204 188 235 227 234 264 302 293 259 229 203 229
1955 242 233 267 269 270 315 364 347 312 274 237 278
1956 284 277 317 313 318 374 413 405 355 306 271 306
1957 315 301 356 348 355 422 465 467 404 347 305 336
1958 340 318 362 348 363 435 491 505 404 359 310 337
1959 360 342 406 396 420 472 548 559 463 407 362 405
1960 417 391 419 461 472 535 622 606 508 461 390 432
```

### Make Inferences
Look at some basic behaviour of the series
```
## make sure its a time series object
> class(AirPassengers)
[1] "ts"

## get its distribution
> summary(AirPassengers)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  104.0   180.0   265.5   280.3   360.5   622.0 

## plot the series
> plot(AirPassengers)
```
<p style='text-align:center'><img src='https://github.com/xinyix/ARIMA/blob/master/data.jpg?raw=true'></p>

 Now we sketch out the general trend by aggregating the series according to years
 ```
 > plot(aggregate(AirPassengers,FUN=mean))
 ```
 <p style='text-align:center'><img src='https://github.com/xinyix/ARIMA/blob/master/aggregate_by_year.jpg?raw=true'></p>

We can also pull out some details of the seasonal effects using boxplot across a single cycle (12 month in this case)
```
> boxplot(AirPassengers~cycle(AirPassengers))
```
 <p style='text-align:center'><img src='https://github.com/xinyix/ARIMA/blob/master/boxplot_for_seasonality.jpg?raw=true'></p>
 
### Try Various ARIMA Models
