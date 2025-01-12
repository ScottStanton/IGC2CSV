# IGC2CSV
Reads an IGC file (a flight log used very commonly in hang gliding and paragliding) and spits out a CSV file with the flight data.

The intention is to make it much easier to look at the flight data in a program like Microsoft Excel without having to write your own parser.

The CSV output also has a bunch of data derived from the data, allowing quick and easy access to stats like distance traveled, per-second climb rate, total distance climbed, etc. Again, the idea here is to be able to pull this data in to Excel and start graphing it immediately without the need to do a bunch of formula work to get at the interesting statistics.

## Installation
The current version of IGC2CSV is a command-line tool that requires Python (tested with 2.7.5) to run. To install, simply extract the program to any convenient directory.

## Usage
You can specify either a single IGC file, or a directory full of IGC files:

    python3 IGC2CSV.py /path/to/file.igc
    python3 IGC2CSV.py /path/to/folder/with/igc/files/

The CSV files will be output in the current working directory

If you add the '-i' flag it will output values in imperial units instead of metric
If the flag is left off then metric units will be used.


## CSV

| Field Name | Metric | Imperial |
| --- | --- | --- |
| DateTime | | |
| Elapsed Time | Seconds | Seconds |
| Latitude | Degrees | Degrees |
| Longitude | Degrees | Degrees |
| Altitude GPS | Meters | Feet |
| Distance Delta | Meters | Feet |
| Distance Total | Meters | Feet |
| Groundspeed | KPH | MPH |
| Groundspeed Peak | KPH | MPH |
| Altitude Delta GPS | Meters | Feet |
| Altitude Delta Pressure | Meters | Feet |
| Climb Speed | Meters/Second | Feet/Minute |
| Climb total | Meters | Feet |
| Max Altitude (flight) | Meters | Feet |
| Min Altitude (flight) | Meters | Feet |
| Distance from Start (linear) | Kilometers | Miles |


# DashWare
Another purpose of this program is to put your flight logs in to a format that DashWare can understand, making it possible to create telemetry overlays on your flight videos.

[Example](http://www.youtube.com/watch?v=KKlZ1oOEYNI&hd=1)

DashWare supports a variety of formats natively, but IGC is not one of them. The included DashWare DataProfile works alongside the output of IGC2CSV to give you access to all of your flight data, *including True Airspeed if your variometer supports it.*

### Advantages over other solutions like converting IGC to NMEA
* Support for True Airspeed, if present in the source data. This was the original reason IGC2CSV was written
* "Maximum reached" for several fields, allowing you to draw things such as red lines indicating the highest altitude reached in the flight *so far* (as opposed to highest reached ever in the flight)
* Some other convenience fields such as Lowest and Highest altitude reached, allowing you to draw instruments showing things such as "altitude above LZ"

### Using the DashWare DataProfile
Copy the IGC2CSV.xml file to your Documents/DashWare/DataProfiles directory.

The DataProfile should automatically detect when you load a compatible CSV in to your DashWare project, but if it does not, you can find it in the list as "IGC2CSV"
