## Some Notes

**docker compose up** = create (if didn't create), and running all of the container that described on that. also they have ability to view logging

**docker compose down** = stop and destroy all of container

**docker compose create** = create the container

**docker compose start** = run the container

**docker compose stop** = stop the container

**docker compose ps** = see whats the container running

**docker compose ls** = see whats docker compose file running and where the location.

**docker compose -f file.yaml (create | start | up | down | stop | build)** = running docker compose with spesific yaml file

merging docker yaml file : 
**docker compose -f base_file.yaml -f file_want_to_merge.yaml (create | start | up | down | stop | build)** = running docker compose with spesific yaml file (more simple in code)