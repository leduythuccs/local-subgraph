# Running subgraph in local

## How to run

Create a `.env` base on `.env.example`.

Make sure that all of the following port are available:

- 8000, 8001, 8020, 8030, 8040: port for subgraph
- 5001: ipfs

Run `docker-compose build` and `docker-compose up`.

- If you are using Mac M1, you might need to clone graph-node repo and rebuild the image, see this: https://github.com/graphprotocol/graph-node/tree/master/docker#running-graph-node-on-an-macbook-m1

After the whole system is up, you can use:

- `http://localhost:8000` to access the subgraph.

## After running

- `git submodule init`
- `git submodule update`

- Go to `example-subgraph` folder and run:

```bash
yarn
yarn codegen
yarn create-local
yarn deploy-local
```

- Then you should see the subgraph docker will start to sync the example subgraph.

- Go to ` http://127.0.0.1:8000/subgraphs/name/example` to make some query!

## Setting

In `docker-compose.yml`, `ETHEREUM_POLLING_INTERVAL` is set to 10 seconds to reduce number of requests to the RPC node.

Might need to changes it to a smaller value later (default is 0.5 secs)

## Note

Subgraph will use a lot of request to the RPC, so make sure that you have enough quota on your account.
