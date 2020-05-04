# mongodb-replset
Easily set up MongoDB 3 node replica set using docker compose

1. Add mongo1, mongo2 and mongo3 to your /etc/hosts

    ```echo "127.0.0.1 mongo1 mongo2 mongo3" | sudo tee -a /etc/hosts```

2. Start docker containers

    ```docker-compose up -d```

3. Initialize replica set cluster

    ```mongo mongo1:30001 --eval rs-init.js```

4. Connect mongo shell (or application) to the replica set

    ```mongo --host rs01/mongo1:30001,mongo2:30002,mongo3:30003```


