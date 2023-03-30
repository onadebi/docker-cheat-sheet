# docker-cheat-sheet

To filter from list of containers (both running and non-running), use below sample command:
## docker ps --all --filter "name=mariadb"

To filter from docker images, one of several ways is to filter by reference, as shown in the example below:
## docker images --filter=reference='**rabbit**'
