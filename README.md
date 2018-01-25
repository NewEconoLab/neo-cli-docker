# neo-cli-docker
use neo-cli easy by docker

## Setp 1

Prepare docker environment

https://docs.docker.com/engine/installation/

## Setp 2

Run Shell to Buld Image 

For Mainnet

<code>
docker build -t neo-cli:v0.1 https://github.com/NewEconoLab/neo-cli-docker.git#:dockerfile/mainnet
</code>


For Testnet

<code>
docker build -t neo-cli-testnet:v0.1 https://github.com/NewEconoLab/neo-cli-docker.git#:dockerfile/testnet
</code>

## Step 3

Run Shell to Run container From Image

For Mainnet

<code>
docker run --rm -it -p 10332:10332 -v /home/neo/cli/0:/home/cli/Chain neo-cli:v0.1 /bin/bash
</code>

For Testnet

<code>
docker run --rm -it -p 20332:20332 -v /home/neo/cli/0:/home/cli/Chain neo-cli-testnet:v0.1 /bin/bash
</code>

## Step 4

Start neo-cli

<code>
cd /home/cli && dotnet neo-cli.dll /rpc
</code>

## Step 5

Mainnet Cli RPC

http://127.0.0.1:10332

Testnet Cli RPC

http://127.0.0.1:20332