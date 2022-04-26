- Docker container example
  id:: 626357d7-2b13-4902-89f7-94a73712b7d6
	-
	- docker-compose.yml file
	  ```yml
	  version: '3.8'
	  services:
	    db:
	      image: postgres
	      container_name: <name_db>
	      env_file:
	        - db.env
	      ports:
	        - 9000:5432
	      volumes: 
	        - db:<path_to_desired_location>
	  volumes:
	    db:
	      driver: local
	  ```
	- db.env file
	  ```env
	  POSTGRES_USER=postgres
	  POSTGRES_PASSWORD=postgres
	  ```