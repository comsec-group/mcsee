# McSee: Evaluating Advanced Rowhammer Attacks and Defenses via Automated DRAM Traffic Analysis

These are the artifacts for the research paper "McSee: Evaluating Advanced Rowhammer Attacks and Defenses via Automated DRAM Traffic Analysis" that is to appear at USENIX Security 2025. This repository provides all the resources necessary to explore, reproduce, and build upon our work.

### Abstract
Our work sheds light on the current state of Rowhammer attacks and defenses by building an automated DRAM traffic analysis platform called McSee. Equipped with this platform, we analyze advanced Rowhammer(-like) attacks on DDR4 and the deployed mitigations in DDR5 systems. We find areas for improvement in existing attacks and show, for the first time, that CPU vendors do not send the necessary RFM commands to DRAM under a Rowhammer workload. We also find that Intel has deployed a pTRR mitigation in its Raptor Lake client CPUs, which we reverse engineer.

###  Metadata

| **Property**  | [![Academic Code](https://img.shields.io/badge/Origin-Academic%20Code-C1ACA0.svg?style=flat)]() [![License: GPL](https://img.shields.io/badge/License-GPLv3-yellow.svg)](https://opensource.org/licenses/gpl-3-0) [![contributions welcome](https://img.shields.io/badge/Contributions-Welcome!-orange.svg?style=flat)]()
| --------------| --------------------------------------------------------------------
| Authors       | Patrick Jattke, Michele Marazzi, Flavien Solt, Max Wipfli, Stefan Gloor, and Kaveh Razavi
| Organization  | ETH Zurich, [COMSEC Group](https://comsec.ethz.ch/)
| Publisher     | [34th USENIX Security Symposium 2025](https://www.usenix.org/conference/usenixsecurity25)
| Webpage       | https://comsec.ethz.ch/mcsee
| Paper         | https://comsec-files.ethz.ch/papers/mcsee_sec25.pdf

## Repositories overview

We bundled all repositories related to McSee in the [mcsee-artifacts](https://github.com/mcsee-artifacts) GitHub organization.

- **Platform & Tools**
   - [**spd-decoder**](https://github.com/mcsee-artifacts/spd-decoder): we show in §6.1 (RDM on DDR5 Devices) that 55% (16/29) of our DDR5 DIMMs advertise valid RFM values but only 14% (4/29) require RFM. We obtained this information by decoding the SPD chip of our DDR5 DIMMs using the SPD reader of this artifact.
   - [**ddr5-udimm-interposer-pcb**](https://github.com/mcsee-artifacts/ddr5-udimm-interposer-pcb): as we explain in §4.1 (Hardware Components), we designed a DDR5 UDIMM interposer with soldering points, which makes attaching the oscilloscope probes easier. This artifact contains the complete PCB design files, enabling simple reproduction of our interposer.
   - **Scope data processing pipeline**
   We describe in §4.2 (DDR4 and DDR5 Command Decoder) and in §4.3 (Software) our scope data processing pipeline that enables McSee's automated DRAM traffic analysis.
      - [**xmldig2csv-converter**](https://github.com/mcsee-artifacts/xmldig2csv-converter): we describe in §4.3 (Software) that a major bottleneck of our pipeline is converting the XMLdig files into CSV files. This artifact contains our parallelized XMLdig-to-CSV converter.
      - [**ddr4-decoder**](https://github.com/mcsee-artifacts/ddr4-decoder): we use the DDR4 decoder in §5 (Analyzing Advanced Attacks) for the analyses of Sledgehammer and Rowpress that we conducted on an Intel Coffee Lake (i7-8700K) system.
      - [**ddr5-decoder**](https://github.com/mcsee-artifacts/ddr5-decoder): we use the DDR5 decoder in §6.2 (DRAM Addressing Functions), §6.3 (RFM on Memory Controllers), and §6.4 (Reverse Engineering Intel's pTRR) that we conducted on Intel Alder Lake (i7-12700K), Intel Raptor Lake (i7-13700K), and an AMD Zen 4 (R7 7700X) system.

- **Experiments**
   - [**mcsee-experiments**](https://github.com/mcsee-artifacts/mcsee-experiments): contains the code and instructions to reproduce the experiments of our paper.
   - [**sledgehammer**](https://github.com/mcsee-artifacts/sledgehammer): a fork of SledgeHammer that exposes an argument to only hammer a certain number of banks and instrumentation for the oscilloscope capture.
   - [**rowpress**](https://github.com/mcsee-artifacts/rowpress): a fork of RowPress with improved REF synchronization and instrumented for scope acquisition. 

## Data

We provide the raw oscilloscope traces to enable reproducibility of our work without requiring access to the McSee platform. Due to size restrictions on GitHub, we provide the data on Zenodo only under following stable URL: https://zenodo.org/records/15610916.

The Zenodo archive contains a snapshot of all the repositories listed above including a `mcsee-data` directory with the data collected from the oscilloscope. This repository follows the same structure as the `mcsee-experiments` repository.


## Citing our paper

```
@inproceedings{jattke2025mcsee,
  title     = {{McSee: Evaluating Advanced Rowhammer Attacks and Defenses via Automated DRAM Traffic Analysis}},
  author    = {Jattke, Patrick and Marazzi, Michele and Solt, Flavien and Wipfli, Max and Gloor, Stefan and Razavi, Kaveh},
  booktitle = {Proceedings of the 34th USENIX Security Symposium (USENIX Security '25)},
  year      = {2025},
  month     = aug,
  publisher = {USENIX Association},
  address   = {Seattle, WA, USA},
  url       = {https://www.usenix.org/conference/usenixsecurity25/presentation/jattke},
}
```

## Citing our code

Please use Zenodo to cite the McSee platform. You can find the stable URL here: https://zenodo.org/records/15610916.

