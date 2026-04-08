# UE1 changes
What was wrong? AMF rejected the setup
* MNC was set to 99 in the nrf yaml, set it to 98 to be compliant with the UE
* changed TAC from 0xa000 to 00ab00 (UE TAC)
* DB subscription insert statemnt is wrong having the old MNC value

**UE1 is up** my5grantester  | time="2026-04-08T14:52:37Z" level=info msg="[UE][DATA] UE is ready for using data plane"

# UE2 Changes:
UE2 was mostly fixed by changes done for UE1, however it needed the adjustment of the database registration to have the proper OPC, and KEY values inside

INSERT INTO `AuthenticationSubscription` (`ueid`, `authenticationMethod`, `encPermanentKey`, `protectionParameterId`, `sequenceNumber`, `authenticationManagementField`, `algorithmId`, `encOpcKey`, `encTopcKey`, `vectorGenerationInHss`, `n5gcAuthMethod`, `rgAuthenticationInd`, `supi`) VALUES
    ('208980000000002', '5G_AKA', '0C0A34601D4F07677303652C0462535B', '0C0A34601D4F07677303652C0462535B', '{\"sqn\": \"000000000000\", \"sqnScheme\": \"NON_TIME_BASED\", \"lastIndexes\": {\"ausf\": 0}}', '8000', 'milenage', '63bfa50ee6523365ff14c1f45f88737d', NULL, NULL, NULL, NULL, '208980000000002');


# UE3
reason for issue oai-amf | [2026-04-08 21:06:25.559] [amf_sbi] [info] Get response with HTTP code (403)
oai-amf | {"error":{"cause":"DNN_DENIED"}}

issue is there is no DNN called oai.ipvr

Reason - bad network slicing setup 

      SST_GNB: de
      SST_UE: 222
      SD: "00007b"

fix - adjust network 1 to be the requested slice
adjustments needed in smf and upf

Done