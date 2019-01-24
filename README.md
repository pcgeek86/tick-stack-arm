# TICK Stack for ARM Devices

Run the InfluxData [TICK stack](https://www.influxdata.com/time-series-platform/) for ARM devices, such as Raspberry Pi 3.

## Prerequisites

* Install [Docker Engine](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
* Install [Docker Compose CLI](https://docs.docker.com/compose/install/)

## Usage

To launch the TICK stack on your ARM device:

```bash
git clone https://github.com/pcgeek86/tick-stack-arm ~/
cd ~/tick-stack-arm
docker-compose up --detach
```

You should see log output similar to the following, after a couple minutes:

```text
pi@pidev:~/tick-stack-arm $ docker-compose up --detach
Creating network "tick-stack-arm_tick-stack" with the default driver
Creating network "tick-stack-arm_default" with the default driver
Creating tick-stack-arm_influxdb_1 ... done
Creating tick-stack-arm_kapacitor_1    ... done
Creating tick-stack-arm_chronograf_1    ... done
Creating tick-stack-arm_telegraf_1      ... done
Creating tick-stack-arm_influxdb-cli_1  ... done
Creating tick-stack-arm_kapacitor-cli_1 ... done
```

Once the stack is up and running, you can access the Chronograf web interface at `http://<pi>:8888`. Complete the setup process, using the container names as the DNS endpoints for InfluxDB (http://influxdb:8086) and Kapacitor (http://kapacitor:9092).

## Removal

If you want to destroy the Docker containers and networks associated with the TICK stack:

```bash
cd ~/tick-stack-arm
docker-compose down
```

**NOTE**: The InfluxDB container will leave behind an additional `./data` directory, containing its application state. You can remove this if you'd like to reset the environment.
