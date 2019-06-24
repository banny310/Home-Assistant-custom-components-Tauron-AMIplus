# Tauron AMIplus sensor

This sensor uses unofficial API to get energy usage data from [*TAURON eLicznik*](https://elicznik.tauron-dystrybucja.pl).

WARNING: Currently it only supports G11 and G12 tariffs.

## Configuration options

| Key | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `name` | `string` | `False` | `Tauron AMIPlus` | Name of sensor |
| `username` | `string` | `True` | - | Username used to login at [*eLicznik*](https://elicznik.tauron-dystrybucja.pl) |
| `password` | `string` | `True` | - | Password used to login at [*eLicznik*](https://elicznik.tauron-dystrybucja.pl) |
| `energy_meter_id` | `string` | `True` | - | ID of energy meter |
| `monitored_variables` | `list` | `True` | - | List of variables to monitor |

### Possible monitored conditions

| Key | Description |
| --- | --- | 
| `zone` | Current zone |
| `consumption_daily` | Daily energy consumption **(for previous day!)** |
| `consumption_monthly` | Monthly energy consumption |
| `consumption_yearly` | Yearly energy consumption |

## Example usage

```
sensor:
  - platform: tauron_amiplus
    name: Tauron AMIPlus
    username: !secret tauron_amiplus.username
    password: !secret tauron_amiplus.password
    energy_meter_id: !secret tauron_amiplus.energy_meter_id
    monitored_variables:
      - zone
      - consumption_daily
      - consumption_monthly
      - consumption_yearly
```

## Instalation

Download [*sensor.py*](https://github.com/PiotrMachowski/Home-Assistant-custom-components-Tauron-AMIplus/raw/master/sensor.py) and [*manifest.json*](https://github.com/PiotrMachowski/Home-Assistant-custom-components-Tauron-AMIplus/raw/master/manifest.json) to `config/custom_compoments/tauron_amiplus` directory:
```bash
mkdir -p custom_compoments/tauron_amiplus
cd custom_compoments/tauron_amiplus
wget https://github.com/PiotrMachowski/Home-Assistant-custom-components-Tauron-AMIplus/raw/master/sensor.py
wget https://github.com/PiotrMachowski/Home-Assistant-custom-components-Tauron-AMIplus/raw/master/manifest.json
```

## FAQ

* **How to get energy meter id?**
  
  To find out value for `energy_meter_id` log in to [_*eLicznik*_](https://elicznik.tauron-dystrybucja.pl). Desired value is in upper-left corner of page (Punkt poboru).