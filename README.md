wget -q -O okp4.sh https://api.nodes.guru/okp4.sh && chmod +x okp4.sh && sudo /bin/bash okp4.sh
source $HOME/.bash_profile

wallet;
okp4d keys add wallet
okp4d q bank balances YOUR_WALLET_ADDRESS
okp4d tx staking create-validator \
--amount=1000000uknow \
--pubkey=$(okp4d tendermint show-validator) \
--moniker="$OKP4_NODENAME" \
--chain-id=okp4-nemeton \
--commission-rate="0.01" \
--commission-max-rate="0.10" \
--commission-max-change-rate="0.01" \
--min-self-delegation="1000000" \
--fees=1000uknow \
--from=wallet \
-y
