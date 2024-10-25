# Nest Finder

MoveApps

Github repository: https://github.com/steffenoppel/MoveAppNestFind

## Description
This app is based on the (R package 'NestTool')[https://github.com/Vogelwarte/NestTool] and is designed for field-work use - namely to find the most likely nest location of a bird that is being tracked with a transmitting device that regularly sends location information to a Movebank project.

## Documentation
To use this app you must be a collaborator or data manager of a Movebank project that receives live location data of active animals. This app will NOT work on historic data, because it will only look for data up to 4 weeks prior to the present date.

You will need to enter your Movebank username, your Movebank password, and the Movebank study name of the study in which the animal location data are stored. There is an optional field where you can enter a second Movebank study if you would like to look at animals from two studies simultaneously.

You will need to provide a time frame (in weeks) as an integer number - this is the time window over which data will be downloaded from Movebank (from the present day up to X weeks previously, with X being the number you have entered in this field).

The last field requires you to enter an error radius (in metres) around a likely nest location. This radius will determine in which radius the residency times will be calculated, i.e. how long an animal remained within that radius or how long it spent outside of this radius. Please consider device accuracy and general movement behaviour of the species when specifying the radius. Default is 50 m.

Once the data have been downloaded the user is presented with a split window with a dropdown menu to select individual birds and the number of locations that should be displayed on the map. A download button allows the user to download a .gpkg file, which can be opened in free GIS applications on mobile devices to facilitate offline navigation. The gpkg file contains the likely nest locations for all individuals, not just the selected one shown in the map, and therefore only needs to be downloaded once.

### Application scope
#### Generality of App usability

This App was developed using data of birds. 

This App was developed to identify nest sites, but can probably be used to identify any kind of regularly used location clusters like roosts, feeding sites, or the place where an animal died (if the transmitter is still providing location information).

We developed this App specifically to assist in finding the nests of Red Kites tracked with GPS-GSM devices, and we have not exhaustively tested how well it works for other species and data sources.

#### Required data properties

This App is only applicable to data that have been recorded in the past 4 weeks. For historic data, the (R package 'NestTool')[https://github.com/Vogelwarte/NestTool] can be used to determine nest location and breeding success. 

The data should have a fix rate of at least several locations per day, both during day and night, and with GPS precision. The location error of the data should be lower than the general movement radius around a nest specified by the user. 

The App should work for any kind of (location) data.

### Input type
The App reads data from Movebank and requires a valid username, password, and the Movebank ID of a study the user has download access to. The remaining input fields are numeric.

### Output type
The App provides a visual map of likely nest locations for all individuals with sufficient data in the selected time period. These locations can also be downloaded in a (.gpkg file)[https://docs.fileformat.com/gis/gpkg/]


### Settings 
`Error radius (in m) of locations around likely nest site` (radius): Defined radius in which the residency times will be calculated. Unit: `metres`.


`Timeframe (number of recent weeks to download data)`: Defined interval over which data will be downloaded and analysed, anchored to the current date. Unit: `weeks`.


### Most common errors
If your data are too big, it is likely that you will get a 'disconnected from server' error message, simply because it took too long to download the data. Try a shorter time duration.

### Null or error handling
Try a shorter time duration by setting the Timeframe to 1 or 2. If your study contains hundreds of animals with tracking data at very high temporal resolution (seconds) then it is possible that the volume of data cannot be processed in this app. Sorry.
