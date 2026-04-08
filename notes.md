# UE1 changes
What was wrong? AMF rejected the setup
* MNC was set to 99 in the nrf yaml, set it to 98 to be compliant with the UE
* changed TAC from 0xa000 to 00ab00 (UE TAC)
* DB subscription insert statemnt is wrong having the old MNC value

**UE1 is up** my5grantester  | time="2026-04-08T14:52:37Z" level=info msg="[UE][DATA] UE is ready for using data plane"