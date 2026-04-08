# UE1 changes
What was wrong? AMF rejected the setup
* MNC was set to 99 in the nrf yaml, set it to 98 to be compliant with the UE
* changed TAC from 0xa000 to 00ab00 (UE TAC)
* DB subscription insert statemnt is wrong having the old MNC value
