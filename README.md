# eos-chronicle-docker
docker-compose simplified running chronicle on different OS. To run chronicle necessary to do several steps:

   1. Download project `git clone https://github.com/EOSTribe/eos-chronicle-docker`
   2. Change folder `cd eos-chronicle-docker`
   3. Provide parameters in docker-compose.yml
   4. Run application `docker-compose up -d`

All parameters pass to chronicle as environmental variables and set provided in section environment in docker-compose.yml  

Build:
`docker-compose -f docker-compose-build.yml build`  
`docker-compose -f docker-compose-build.yml up`  