# OGN Data Analysis

[Open Glider Network](https://www.glidernet.org/) (OGN) is an open source
project that powers ground stations capable of receiving aircraft locations and
relaying them over the internet. Data is freely available for any one to stream
by connecting to the appropriate APRS servers.

The analysis itself and the accompanying text is available in
[analysis.ipynb](analysis.ipynb).


## Data and methods

The data used in this analysis was collected between 2017-08-09	and 2018-05-19
using the [ogn-lib](https://github.com/akolar/ogn-lib) package. On 2018-05-20
OGN introduced [new data usage
rules](https://www.glidernet.org/ogn-data-usage/), which effectively prohibit
performing any kind of data manipulation after 24 hours have passed since its
collection, therefore any data collected after this date is not included in this
document. Also keep in mind that some days are missing due to technical
difficulties on the clients side.

Size of the exported database is 80 GB (CSV without compression). For the
purposes of this analysis the data was uploaded and stored on an Amazon Redshift
cluster. Returned aggregates were further processed using pandas and visualized
with either matplotlib or seaborn. 

A record received from OGN (usually -- not all receivers provide all the fields)
contains the following information:

- device ID
- receiver ID
- timestamp
- latitude and longitude
- ground speed
- heading
- altitude
- vertical speed

An example of such record is

```
FLRDDFB2A>APRS,qAS,LFPF:/181325h4849.83N\00204.65E^292/072/A=001115 !W66! id22DDFB2A +040fpm +0.0rot 10.2dB 0e -6.7kHz gps2x3
```
