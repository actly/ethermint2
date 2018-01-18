
source $HOME/.gvm/scripts/gvm
gvm use go1.9.2 —-default


install:    (tendermint with v0.15.0)
git clone git@github.com:3rdStone/ethermint2.git


mkdir -p ~/.ethermint/tendermint/
cp -r $GOPATH/src/github.com/3rdStone/ethermint2/setup/* ~/.ethermint/


init:
tendermint init --home ~/.ethermint/tendermint
ethermint --datadir ~/.ethermint init ~/.ethermint/genesis.json


vim tendermint/genesis.json
vim tendermint/config.toml


run:
tendermint --home ~/.ethermint/tendermint node
ethermint --datadir ~/.ethermint --rpc --rpcaddr=0.0.0.0 --ws --wsaddr=0.0.0.0 --rpcapi eth,net,web3,personal,admin


run--with-tendermint
ethermint --datadir ~/.ethermint --rpc --rpcaddr=0.0.0.0 --ws --wsaddr=0.0.0.0 --rpcapi eth,net,web3,personal,admin --with-tendermint tendermint
