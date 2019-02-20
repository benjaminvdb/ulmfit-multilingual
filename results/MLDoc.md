
## Supervised classification results on MLDoc
| Model          |   en      |   de      |   es      |   fr      |   it      |   ja      |   ru      |   zh       |
|----------------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|------------|
|LASER 0 shot    |   80.75   |   87.03   |   82.60   |   82.83   |   73.25   |   60.95   |   68.83   |  72.90     |
|LASER           |   90.73   |   92.70   |   88.75   |   90.80   |   85.93   |   85.15   |   84.65   |  88.98     |
|MultiCCA        |   92.2    |   93.70   |   94.45   |   92.05   |   85.55   |   85.35   |   85.65   |  87.30     |
|Bert Multi      |   93.23   |   94.0    |   95.15   |   93.20   |   85.82   |   87.48   |  86.85    |  90.72     |
|ULMFiT L30k-100 |           |   91.35   |   83.32   |   88.77   |   77.99   |   71.12   |   72.20   |            |
|ULMFiT L30k     |           |   95.4    |   95.15   |   93.67   |   88.42   |   89.20   | **87.27** |  90.20     |
|ULMFiT sp-fixed |           |  **95.6** |   94.80   |   94.20   |   88.52   |   88.72   |   86.85   |  90.47     |
|ULMFIT Q15k 1cyc| **94.62** | **95.65** |   95.15   | **94.42** | **89.92** | **89.60** |           |  90.78/89.82  |
|ULMFIT L30k 1cyc|           |           | **95.95** |           |           |           |           | **92.02**  |
- L30k  -  LSTM sp30k trained using gradual unfreezing
- L30k-100 -  --||-- **on 100 samples**
- ULMFiT sp-fixed - --||-- with fixed tokenization 
- Q15k 1cyc - QRNN sp15k trained using 1cycle learning rate schedule
- L30k 1cyc - LSTM sp30k trained using 1cycle learning rate schedule 

## Zero shot approaches - LSTM

| Model                |    de      |    es      |   fr      |   it      |   ru      |   zh      |
|----------------------|------------|------------|-----------|-----------|-----------|-----------|
| LASER-de             |            |    81.40   |   81.50   |   74.53   |   64.58   |   73.20   |
| LASER-fr             |    88.75   |    80.12   |           |   72.58   |   67.35   |   79.40   |
| LASER-en             |    87.65   |    75.48   |   84.00   |   71.18   |   66.58   |   76.65   |
|                      |            |            |           |           |           |           |
| ULMFiT on LASER-de   |            |  **85.50** |   87.37   | **78.75** |   66.95   |   72.32   |
| ULMFiT on LASER-fr   |    92.22   |    81.00   |           |   76.88   |   68.33   | **84.65** |
| ULMFiT on LASER-en   |  **92.95** |    80.50   | **88.78** |   76.20   | **70.05** |   80.45   |
|                      |            |            |           |           |           |           |
| % impr over LASER-de |            |    22%     |   32%     |   17%     |   7%      |  *-3%*    |
| % impr over LASER-fr |    31%     |    4%      |           |   16%     |   3%      |   25%     |
| % impr over LASER-en |    43%     |    20%     |   30%     |   17%     |   10%     |   16%     |
| ULMFiT 100 for comp. |    91.35   |    83.32   |   88.77   |   77.99   |   71.12   |           |
|                      |            |            |           |           |           |           |
| Bert Multilingual-EN |    74.50   |   61.85    |   69.77   |   57.73   |   51.10   |  64.08    |


### From Laser trained on French data
| Model Name                | de    | es    | fr | it    | ru    | zh    |
|---------------------------|-------|-------|----|-------|-------|-------|
| LASER fr 10k              | 91.65 | 81.05 |    | 75.08 | 70.73 | 76.33 |
| LASER fr 1k               | 88.75 | 80.12 |    | 72.58 | 67.35 | 79.4  |
| ULMFiT 10k on LASER-fr10k | 94.48 | 84.10 |    | 77.93 | 72.87 | 84.53 |
| ULMFiT 10k on LASER-fr1k  | 92.30 | 82.10 |    | 75.52 | 69.52 | 85.55 |
| ULMFiT 1k on LASER-fr1k   | 92.22 | 81.00 |    | 76.88 | 68.33 | 84.65 |
|                           |       |       |    |       |       |       |
| Impr 10k over 10k         | 34%   | 16%   |    | 11%   | 7%    | 35%   |
| Impr 10k over 1k          | 32%   | 10%   |    | 11%   | 7%    | 30%   |
| Impr 1k over 1k           | 31%   | 4%    |    | 16%   | 3%    | 25%   |

### From Laser trained on German data
| Model Name                | de | es    | fr    | it    | ru    | zh    |
|---------------------------|----|-------|-------|-------|-------|-------|
| LASER de 10k              |    | 83.5  | 82.85 | 76.6  | 68.8  | 73.12 |
| LASER de 1k               |    | 81.4  | 81.5  | 74.53 | 64.58 | 73.2  |
| ULMFiT 10k on LASER-de10k |    | 86.92 | 87.17 | 79.35 | 70.15 | 78.15 |
| ULMFiT 10k on LASER-de1k  |    | 84.65 | 87.48 | 78.70 | 67.65 | 77.50 |
| ULMFiT 1k on LASER-de1k   |    | 85.5  | 87.37 | 78.75 | 66.95 | 72.32 |
|                           |    |       |       |       |       |       |
| Impr 10k over 10k         |    | 21%   | 25%   | 12%   | 4%    | 19%   |
| Impr 10k over 1k          |    | 17%   | 32%   | 16%   | 9%    | 16%   |
| Impr 1k over 1k           |    | 22%   | 32%   | 17%   | 7%    | -3%   |

### From Laser trained on English data 
| Model Name                | de    | es    | fr    | it    | ru    | zh    |
|---------------------------|-------|-------|-------|-------|-------|-------|
| LASER en 10k              | 87.43 | 77.38 | 78.7  | 72.53 | 67.7  | 75.18 |
| LASER en 1k               | 87.65 | 75.48 | 84    | 71.18 | 66.58 | 76.65 |
| ULMFiT 10k on LASER-en10k | 92.05 | 80.05 | 86.95 | 76.65 | 70.57 | 80.85 |
| ULMFiT 10k on LASER-en1k  | 91.80 | 80.10 | 88.67 | 77.32 | 70.25 | 82.73 |
| ULMFiT 1k on LASER-en1k   | 92.95 | 80.50 | 88.78 | 76.20 | 70.05 | 80.45 |
|                           |       |       |       |       |       |       |
| Impr 10k over 10k         | 37%   | 12%   | 39%   | 15%   | 9%    | 23%   |
| Impr 10k over 1k          | 34%   | 19%   | 29%   | 21%   | 11%   | 26%   |
| Impr 1k over 1k           | 43%   | 20%   | 30%   | 17%   | 10%   | 16%   |


All ULMFiT examples above were trained on 1k training data generated by a LASER classification model 

## Noise resistance

| Model                           |   en       |   de      |   es      |   fr      |   it      |   ja      |   ru      |   zh       |
|---------------------------------|------------|-----------|-----------|-----------|-----------|-----------|-----------|------------|
|LASER 0 shot                     | 80.75 (en) | 87.03 (fr)| 82.60 (it)| 82.83 (de)| 73.25 (de)| 60.95 (en)| 68.83 (it)| 72.90 (de) |
|ULMFiT                           |            |  **95.4** | **95.15** | **93.67** | **88.42** | **89.20** | **87.27** |            | 
| % of noise                      | 20%        |   13%     |  18%      | 18%       | 27%       | 40%       | 32%       | 28%        | 
|ULMFiT trained on 1k noisy exmp. |            |   94.49   |  93.12    | 90.49     | 83.72     | 74.72     | 75.67     | |

