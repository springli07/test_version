# MasterCube x86-64 Formal Metric Report

- Performance timing seconds per point: `3`
- Peak RSS memory sampling run seconds: `0.10`
- Static memory: `text + data + bss` from `size`.
- Peak memory: sampled from `/proc/<pid>/status` `VmRSS`; process-level RSS including benchmark overhead.

## Functional Correctness

| Implementation | Status | Cases | Mismatches |
| --- | --- | ---: | ---: |
| Performance-optimized | PASS | 51 | 0 |
| Resource-optimized | PASS | 51 | 0 |
| AVX512 | SKIPPED | 0 | 0 |

## Performance: Cycles Per Byte

| architecture | algorithm | implementation_type | 32B | 128B | 512B | 1024B | 4096B | 8192B | 16384B | 65536B |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| X86-64 | MasterCube-512 | Reference | 268.780201 | 134.277910 | 85.289692 | 77.183664 | 75.407947 | 73.820203 | 70.461421 | 72.944925 |
| X86-64 | MasterCube-768 | Reference | 564.874167 | 195.607254 | 118.356366 | 103.060050 | 100.078297 | 98.231886 | 97.629621 | 96.056596 |
| X86-64 | MasterCube-1024 | Reference | 877.407112 | 351.668395 | 189.871527 | 157.041541 | 139.110430 | 141.567236 | 144.658524 | 139.245557 |
| X86-64 | MasterCube-512 | Performance-optimized | 31.300273 | 13.357990 | 8.225062 | 7.424181 | 7.015593 | 6.890538 | 6.707208 | 6.943617 |
| X86-64 | MasterCube-768 | Performance-optimized | 57.829055 | 20.581800 | 11.794305 | 10.384817 | 9.504284 | 9.043119 | 9.157886 | 9.091778 |
| X86-64 | MasterCube-1024 | Performance-optimized | 87.384067 | 34.551900 | 19.897960 | 16.910678 | 15.195618 | 15.068662 | 14.842907 | 14.607604 |
| X86-64 | MasterCube-512 | Resource-optimized | 36.186000 | 16.228907 | 9.750754 | 8.575984 | 8.573031 | 8.332615 | 8.429923 | 8.043190 |
| X86-64 | MasterCube-768 | Resource-optimized | 66.734189 | 24.403040 | 13.628846 | 12.594405 | 11.366802 | 11.499668 | 11.552302 | 11.285890 |
| X86-64 | MasterCube-1024 | Resource-optimized | 98.135886 | 40.425853 | 23.840492 | 20.298010 | 17.595253 | 17.843815 | 17.644175 | 17.460099 |

## Performance: Cycles Per Block / MiB/s

| architecture | algorithm | implementation_type | 32B | 128B | 512B | 1024B | 4096B | 8192B | 16384B | 65536B |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| X86-64 | MasterCube-512 | Reference | 8600.97/8.58 | 17187.57/17.18 | 43668.32/27.05 | 79036.07/29.89 | 308870.95/30.60 | 604735.10/31.25 | 1154439.92/32.74 | 4780518.60/31.63 |
| X86-64 | MasterCube-768 | Reference | 18075.97/4.08 | 25037.73/11.79 | 60598.46/19.49 | 105533.49/22.39 | 409920.70/23.05 | 804715.61/23.49 | 1599563.71/23.63 | 6295165.08/24.02 |
| X86-64 | MasterCube-1024 | Reference | 28077.03/2.63 | 45013.55/6.56 | 97214.22/12.15 | 160810.54/14.69 | 569796.32/16.58 | 1159718.80/16.30 | 2370085.26/15.95 | 9125596.82/16.57 |
| X86-64 | MasterCube-512 | Performance-optimized | 1001.61/73.71 | 1709.82/172.72 | 4211.23/280.50 | 7602.36/310.76 | 28735.87/328.86 | 56447.29/334.83 | 109890.90/343.98 | 455056.88/332.27 |
| X86-64 | MasterCube-768 | Performance-optimized | 1850.53/39.90 | 2634.47/112.10 | 6038.68/195.61 | 10634.05/222.16 | 38929.55/242.75 | 74081.23/255.13 | 150042.80/251.93 | 595838.76/253.76 |
| X86-64 | MasterCube-1024 | Performance-optimized | 2796.29/26.40 | 4422.64/66.77 | 10187.76/115.95 | 17316.53/136.43 | 62241.25/151.83 | 123442.48/153.11 | 243186.19/155.44 | 957323.94/157.94 |
| X86-64 | MasterCube-512 | Resource-optimized | 1157.95/63.76 | 2077.30/142.16 | 4992.39/236.61 | 8781.81/269.02 | 35115.13/269.11 | 68260.78/276.88 | 138115.86/273.68 | 527118.50/286.84 |
| X86-64 | MasterCube-768 | Resource-optimized | 2135.49/34.57 | 3123.59/94.54 | 6977.97/169.28 | 12896.67/183.19 | 46558.42/202.97 | 94205.28/200.63 | 189272.92/199.71 | 739632.09/204.43 |
| X86-64 | MasterCube-1024 | Resource-optimized | 3140.35/23.51 | 5174.51/57.07 | 12206.33/96.77 | 20785.16/113.66 | 72070.16/131.12 | 146176.53/129.30 | 289082.16/130.76 | 1144265.05/132.14 |

## Static Memory Footprint

| Implementation | text | data | bss | static bytes | file bytes |
| --- | ---: | ---: | ---: | ---: | ---: |
| Reference | 57302 | 712 | 16 | 58030 | 66664 |
| Performance-optimized | 23639 | 720 | 16 | 24375 | 33904 |
| Resource-optimized | 14636 | 712 | 16 | 15364 | 22016 |
| AVX512 | 39998 | 712 | 16 | 40726 | 50264 |

## Peak Memory Footprint

| Implementation | Status | Max RSS KB | Max RSS Bytes |
| --- | --- | ---: | ---: |
| Reference | PASS | 1464 | 1499136 |
| Performance-optimized | PASS | 3140 | 3215360 |
| Resource-optimized | PASS | 1500 | 1536000 |
| AVX512 | SKIPPED | 0 | 0 |

## Data Size And Rounds

| Algorithm | Digest size bytes | Core rounds | Interaction rounds |
| --- | ---: | ---: | --- |
| MasterCube-512 | 64 | 18 | N/A for hash |
| MasterCube-768 | 96 | 18 | N/A for hash |
| MasterCube-1024 | 128 | 18 | N/A for hash |

AVX512 runtime data is skipped because this CPU does not report `avx512f`, `avx512bw`, and `avx512vl`, or `RUN_AVX512` was not enabled.
