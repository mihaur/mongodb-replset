# mongodb-replset

Set up MongoDB replica set using docker and docker-compose

## 1 node replica set

1. Start mongo in a contaner 

    ```docker run --name mongo -d --restart unless-stopped -v ~/mongo-data:/var/lib/mongodb:rw -p 27017:27017 mongo:4.2.6 --bind_ip_all --replSet rs01```

1. Initialize replica set single node
    ```mongo --eval 'rs.initiate()'```

1. Connect mongo shell (or application) to the replica set

    ```mongo rs01```
    ```mongo 'localhost?replSet=rs01'```


## 3 node replica set

1. Add mongo1, mongo2 and mongo3 to your /etc/hosts

    ```echo "127.0.0.1 mongo1 mongo2 mongo3" | sudo tee -a /etc/hosts```

1. Start docker containers

    ```docker-compose up -d```

1. Initialize replica set cluster

    ```mongo mongo1:30001 --eval rs-init.js```

1. Connect mongo shell (or application) to the replica set

    ```mongo --host rs01/mongo1:30001,mongo2:30002,mongo3:30003```
