# Welcome to ParkBot :car::robot:
ParkBot is a helpful command line tool for quick search on parking spot data. This tool allows users to locate parking spots by state, minimum hourly price, and maximum hourly price. Keep reading for instructions on using the tool, installation, and customizing the tool for your own parking spot search needs.

## Table of Contents:
* [Technologies](#technologies)
* [Installation](#installation)
* [ParkBot Commands](#commands)
* [Error Handling](#debug)

## <a id="technologies"></a>Technologies ##
ParkBot requires local installation of Python (version 2.7.10 or higher). If you're unsure, check out this [python installation guide](https://wiki.python.org/moin/BeginnersGuide/Download). ParkBot also uses the argparse Python module.

## <a id="installation"></a>Installing & Using ParkBot ##
To use ParkBot, download this project or clone the repository to your local machine: 

`git clone https://github.com/mmdurnin/ParkBot.git`

## <a id="commands"></a>ParkBot Commands ##
ParkBot requires 4 arguments from the command line:
1. **Summon ParkBot** with ```./parkbot``` (Be sure to alter this command if you are not cd'd into the ParkBot repo)
2. **Tell ParkBot which JSON file it should reference** with the name of the JSON file: `airgarage-data.json`
3. **Set ParkBot filter type** with one of the three commands:

    `locate`: search parking spots by location (state)
    
    `find_price_hourly_lte`: search parking spots by max hourly price, inclusive
    
    `find_price_hourly_gt`: search parking spots by min hourly price, exclusive
    
4. **Provide argument** depending on previous command:

    Used with `locate`: provide two letter abbreviation for state, e.g.: `CA`
    
    Used with `find_price_hourly_lte`: provide max price query, **in cents**, e.g.: `500` for parking rates $5.00 or less
    
    Used with `find_price_hourly_gt`: provide min price query, **in cents**, e.g.: `200` for parking rates starting at $2.01
    
### Example
```
> ./parkbot airgarage-data.json locate CA
```
```
Church of 8 Wheels, Sweetgreen, Sandwiches n More, AirGarage HQ, Walgreens, The Salon, Archer Salon
```
        
## <a id="debug"></a>Error Handling ##
#### Too Few Arguments:
ParkBot will only understand commands that follow the format listed above. You must specify the `./parkbot` script, the JSON file, the command type and the argument. If you do not provide these 4 commands, ParkBot will let you know: `error: too few arguments`

#### Mispellings:
* Mispelling the JSON file name will result in the following message `Invalid argument: could not find file 'argarage-data.json'`.
* Mispelling the filter type command (`locate`, `find_price_hourly_lte`, `find_hourly_gt`) will result in a helpful message from parkbot, e.g.: `error: argument search_command: invalid choice: 'lcate' (choose from 'locate', 'find_price_hourly_lte', 'find_price_hourly_gt')`.
* Mispelling the last argument will be interpreted as no results matching query and will return nothing.