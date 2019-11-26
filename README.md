# BHG solidmation PHP API
Solidmation &amp; BGH Smart Control Kit PHP REST API for air conditioner

## Usage

```php
define("BGH_USER", "XXXXX"); //Login email
define("BGH_PASS", "XXXXX"); //Login password

require 'bgh.class.php';

$bgh = new BGH();
/* Use this if you want to get your device list or use another endpointID instead of first */
$devices = $bgh->getDevices(); 

$bgh->sendCommand(array(
	"temperature" => 17,   //Set temperature, default 24
	"fan" => 3,            //Set 1-3 (254 for auto), default auto
	"endpoint" => 39282,   //Set endpoint, default first endpoint
	"mode" => "on"         //Set on/off, default on
));

/* Turn on and set it to 19° */
$bgh->sendCommand(array(
	"temperature" => 19
));

/* Turn fan on max */
$bgh->sendCommand(array(
	"fan" => 3
));

/* Turn off */
$bgh->sendCommand(array(
	"mode" => "off"
));
```

### Commands
#### returnToken _(null)_
Get BGH private token
#### getHomeId _(null)_
Get the ID of your home
#### getDevices _(null)_
Get a list of devices on your home, including ID, room temperature, air conditioner preset, and status
```php
Array
(
    [0] => Array
        (
            [endpointID] => 39282
            [turned] => 1
            [room] => 30.2
            [air] => 17
            [name] => Terraza
            [device] => BGH Smart Control Kit
            [homeID] => 27622
        )

)
```
#### sendCommand _(Array)_
Send command to air conditioner

## License

MIT License

2017
