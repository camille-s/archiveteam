# run usgovernment-grab with docker compose

This is a quick way to run multiple [Archive Team warrior containers](https://wiki.archiveteam.org/index.php/Running_Archive_Team_Projects_with_Docker) for the [usgovernment-grab](https://github.com/ArchiveTeam/usgovernment-grab) project using docker compose. The specs take a username to be used on the [leaderboard](https://tracker.archiveteam.org/usgovernment).

To run it, put your username in an environment variable called `ATUSER`. The simplest way is to write a file `.env` that contains

```
ATUSER=xxusername
```

with whatever username you want to use.

Then run

```
docker compose -f docker-compose.yml up
```

with whatever [additional flags](https://docs.docker.com/reference/cli/docker/compose/up/) you want. By default this runs 10 warrior containers at once, each with a queue of 3 tasks. The overhead is pretty low, so you can scale up as you'd like by adding the flag `--scale xx` with however many containers (I've easily run 25 at once).

To stop it safely (i.e. closing out all the queues before killing the containers), adjust the Archive Team [recommendation](https://wiki.archiveteam.org/index.php/Running_Archive_Team_Projects_with_Docker#Stopping_containers) for `docker compose`:

```
docker compose kill --signal SIGINT
```

That's it! Otherwise make sure your computer stays on (I use [caffeine](https://launchpad.net/caffeine)) and online.
