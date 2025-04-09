# TP Analysis


## Data Location

The data lives in dunegpvms: /pnfs/dune/scratch/users/kwawrows/singlee_n50k/tps/



The files contain TPs generated with all three algorithms (this was part of the threshold scan study, so some thresholds are way too low). Decent ranges for analysis where you don't end up with a lot og noise are:

- **Simple threshold**: 20-30 ADC
- **Running sums**: 30-40 ADC

If you want to analyse a run with a specific threshold or algorithm, you need to call the appropriate producer in the analser fcl. For example, use `tpmakerTPC30RS` for a 30 ADC threshold run with Running Sum.

## TP producers 

- `RunTrigger.. | tpmakerTPC35RS...` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 40
- `RunTrigger.. | tpmakerTPC30RS...` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 2021
- `RunTrigger.. | tpmakerTPC30AbsRS` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 320
- `RunTrigger.. | tpmakerTPC40RS...` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 53
- `RunTrigger.. | tpmakerTPC35AbsRS` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 62
- `RunTrigger.. | tpmakerTPC10.....` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 756530
- `RunTrigger.. | tpmakerTPC20.....` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 193
- `RunTrigger.. | tpmakerTPC25AbsRS` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 3516
- `RunTrigger.. | tpmakerTPC20AbsRS` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 32934
- `RunTrigger.. | tpmakerTPC35RS...` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 202
- `RunTrigger.. | tpmakerTPC20RS...` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 126472
- `RunTrigger.. | tpmakerTPC30.....` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 44
- `RunTrigger.. | tpmakerTPC15.....` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 19838
- `RunTrigger.. | tpmakerTPC15RS...` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 621178
- `RunTrigger.. | tpmakerTPC25.....` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 45
- `RunTrigger.. | tpmakerTPC15AbsRS` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 232582
- `RunTrigger.. | tpmakerTPC40AbsRS` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 49
- `RunTrigger.. | tpmakerTPC25RS...` | std::vector<dunedaq::trgdataformats::TriggerPrimitive> | 19051

## Analyser

The analyser can be found in the TriggerAna repo under `TPGAna_module.cc`. 

### Example FCL for running the analyser:
Example fcls for running the analyser on TP output are in tpgtest_fcls. You should be able to run them with something like

```bash
lar -c runana_ST.fcl -S /pnfs/dune/scratch/users/kwawrows/singlee_n50k/tps/files_out.list -n 200
```

The repository also has an example notebook (imaginatively named ExampleNotebook.ipynb) which shows how to read and process the resulting TTree. 
