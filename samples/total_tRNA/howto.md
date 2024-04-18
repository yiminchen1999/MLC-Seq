## samples

### intact samples
https://github.com/rnamodifications/MLC-Seq/tree/main/samples/total_tRNA/Control

### acid degraded samples
https://github.com/rnamodifications/MLC-Seq/tree/main/samples/total_tRNA/AcidDeg

## preprocessing the datasets
Different datesets come with different intensity scales. We align them to the strongest one. Here are the steps:
1. For each dataset, get the strongest intensity from the intact mass area (with mass greater then 23000 Da). 
2. Choose the top one among those strongest intensities.
3. Compare to the top intensity, we can calculate the calibrate ratio for each dataset.
4. Apply the calibrate ratio of each dataset to all the data fragments inside that particular dataset.
5. Combine the calibrated datasets.
6. Drop duplicated fragments based on the following rules.
    - round the masses of all fragments to integers.
    - put the identical masses into the same group. 
    - inside each group, keep the fragment with the highest intensity only. The rest in the group were treated as duplicated ones, remove them.

## tRNA reference
We use Yeast tRNAs sequences retrieved from the database:
https://tpsic.igcz.poznan.pl/info/start/

## preparing the data for panel a
1. Calculate the theoretical monoisotopic mass for each sequence, and the ones for their Amino-Acid-tailed, CC-tailed, C-tailed isoforms as well. Basically, we have 4 monoisotopic masses for each tRNA sequence.
2. Match the theoretical monoisotopic masses with the dataset of intact samples (all the fragments with masses greater than 23000 Da), find out the matched ones. We use 10 PPM as the cutoff, for example, if the masses of two fragments (one from the theoretical masses list, and the other from the sample's intact dataset) are close enough, in other words, their PPM is within 10, then we can say that the fragment from the dataset is matched with the theoretical mass of a particular tRNA sequence.

					
|  AA | Anticodon   | Mass_CCA | Mass_CC | Mass_C | MatchedMass |Intensity |
| ---- | ----- | ------- | ------- | ------- | ------- | ------- |
| Glu | 3UC | 24175.1764 | 23846.1239 | 23541.0826 | 23541.1338 | 2135534.6648 |
| Asp | GUC | 24233.1744 | 23904.1219 | 23599.0806 | 23599.1584 | 11414249.652 |
| Trp | BCA | 24242.2728 | 23913.2203 | 23608.179 | 23608.1611 | 1685355.1005 |
| Cys | GCA | 24302.2574 | 23973.2049 | 23668.1636 | 23668.1995 | 3375144.6839 |
| Arg | 1CU | 24443.3114 | 24114.2589 | 23809.2176 | 23809.1639 | 217632.4722 |
| Glu | 3UC | 24175.1764 | 23846.1239 | 23541.0826 | 23846.2075 | 6495562.9893 |
| Asp | GUC | 24233.1744 | 23904.1219 | 23599.0806 | 23904.2222 | 37320266.67 |
| Trp | BCA | 24242.2728 | 23913.2203 | 23608.179 | 23913.1541 | 3794563.515 |
| His | GUG | 24570.2684 | 24241.2159 | 23936.1746 | 23936.2036 | 189300.4788 |
| Lys | CUU | 24707.3261 | 24378.2736 | 24073.2323 | 24073.2903 | 1891751.21 |
| Arg | 1CU | 24443.3114 | 24114.2589 | 23809.2176 | 24114.315 | 5920964.077 |
| Val | IAC | 24789.2969 | 24460.2444 | 24155.2031 | 24155.2734 | 7719109.54 |
| Asp | GUC | 24233.1744 | 23904.1219 | 23599.0806 | 24233.281 | 4174695.3487 |
| His | GUG | 24570.2684 | 24241.2159 | 23936.1746 | 24241.1792 | 1832309.2905 |
| Ile | PAP | 24602.3299 | 24273.2774 | 23968.2361 | 24273.312 | 1235001.0294 |
| Val | &AC | 24920.4152 | 24591.3627 | 24286.3214 | 24286.3263 | 2037109.39 |
| Ala | IGC | 24616.2473 | 24287.1948 | 23982.1535 | 24287.1407 | 3226765.9583 |
| Arg | ICG | 24625.3695 | 24296.317 | 23991.2757 | 24296.2919 | 5667266.32 |
| Lys | CUU | 24707.3261 | 24378.2736 | 24073.2323 | 24378.3365 | 735747.34 |
| Trp | BCA | 24242.2728 | 23913.2203 | 23608.179 | 24428.3738 | 4639409.74 |
| Thr | IGU | 24775.4124 | 24446.3599 | 24141.3186 | 24446.2909 | 2222308.5949 |
| Val | IAC | 24789.2969 | 24460.2444 | 24155.2031 | 24460.1541 | 31800269.0543 |
| Lys | 3UU | 24801.3237 | 24472.2712 | 24167.2299 | 24472.2367 | 2809040.192 |
| Val | CAC | 24475.293 | 24146.2405 | 23841.1992 | 24475.1661 | 1291704.5393 |
| His | GUG | 24570.2684 | 24241.2159 | 23936.1746 | 24570.3344 | 2875963.93 |
| Val | &AC | 24920.4152 | 24591.3627 | 24286.3214 | 24591.3995 | 2364837.69 |
| Ala | IGC | 24616.2473 | 24287.1948 | 23982.1535 | 24616.4051 | 680890.891 |
| Tyr | GPA | 25334.5569 | 25005.5044 | 24700.4631 | 24700.485 | 3066189.0039 |
| Asn | GUU | 25051.4371 | 24722.3846 | 24417.3433 | 24722.3175 | 5121419.199 |
| Ini | CAU | 24763.4826 | 24434.4301 | 24129.3888 | 24763.4346 | 1962948.7824 |
| Val | IAC | 24789.2969 | 24460.2444 | 24155.2031 | 24789.2351 | 1103021.9932 |
| Lys | 3UU | 24801.3237 | 24472.2712 | 24167.2299 | 24801.4351 | 211882.0194 |
| Tyr | GPA | 25334.5569 | 25005.5044 | 24700.4631 | 25005.5427 | 8963900.0281 |
| Asn | GUU | 25051.4371 | 24722.3846 | 24417.3433 | 25051.48 | 983478.55 |
| Tyr | GPA | 25334.5569 | 25005.5044 | 24700.4631 | 25334.6049 | 1037639.12 |
| Leu | CAA | 27549.7278 | 27220.6753 | 26915.634 | 26915.6869 | 1805517.16 |
| Ser | IGA | 27657.7223 | 27328.6698 | 27023.6285 | 27023.6672 | 684270.91 |
| Ser | GCU | 27675.6953 | 27346.6428 | 27041.6015 | 27041.6361 | 63260.58 |
| Leu | UAG | 27541.6625 | 27212.61 | 26907.5687 | 27212.6611 | 4432876.16 |
| Leu | CAA | 27549.7278 | 27220.6753 | 26915.634 | 27220.7109 | 11090565.6448 |
| Ser | IGA | 27657.7223 | 27328.6698 | 27023.6285 | 27328.6208 | 1516835.4023 |
| Ser | GCU | 27675.6953 | 27346.6428 | 27041.6015 | 27346.7309 | 1958041.137 |
| Ser | &GA | 27678.769 | 27349.7165 | 27044.6752 | 27349.7559 | 1788359.3313 |
| Leu | UAG | 27541.6625 | 27212.61 | 26907.5687 | 27541.7113 | 642288.36 |
| Leu | CAA | 27549.7278 | 27220.6753 | 26915.634 | 27549.7569 | 1744555.7087 |
| Ser | IGA | 27657.7223 | 27328.6698 | 27023.6285 | 27657.7467 | 2247455.0707 |
| Ser | &GA | 27678.769 | 27349.7165 | 27044.6752 | 27678.8148 | 259439.64 |
| Leu | ~AA | 28365.8754 | 28036.8229 | 27731.7816 | 27731.8277 | 516253.8593 |
| Leu | ~AA | 28365.8754 | 28036.8229 | 27731.7816 | 28036.8795 | 3137161.09 |
| Leu | ~AA | 28365.8754 | 28036.8229 | 27731.7816 | 28365.9112 | 249038.4342 |


## preparing the data for panel b
Based on the matched fragments from panel a, we do the following steps:
1. To avoid a messy figure, we use 1E6 as a cutoff to filter the matched fragments by intensity.
2. We get all the fragment pairs which have a mass difference equals to nucletide A or C, that's 329.05 Da and 305.04 Da respectively.

## preparing the data for panel c
Based on the matched fragments from panel a, compare the masses of fragments with ones in the intact sample, if we observed a pair of masses which has a mass difference equals to a methylation, 14.01 Da, we can say that these two fragments might be the partial methylation.

|  tRNA | Anticodon   | Mass1 | Mass2 |
| ---- | ----- | ------- | ------- |
| Cys	| GCA	| 23668.199499	| 23682.220331	|
| His	| GUG	| 24241.179186	| 24255.295957	|
| Ala	| IGC	| 24273.312050	| 24287.140688	|
| Ala	| IGC	| 24287.140688	| 24273.312050	| 
| Arg	| ICG	| 24296.291941	| 24310.344269	| 
| Val	| IAC	| 24446.290921	| 24460.154130	|
| Val	| IAC	| 24460.154130	| 24474.178956	| 
| His	| GUG	| 24570.334426	| 24584.334969	| 
| Asn	| GUU	| 24722.317490	| 24736.454737	| 
| Asn	| GUU	| 25051.480023	| 25065.490821	| 
| Leu	| ~AA	| 27731.827692	| 27717.836119	| 
| Leu	| ~AA	| 28036.879528	| 28022.834820	| 
| Leu	| ~AA	| 28365.911214	| 28351.856919	| 


## preparing the data for panel d
We match the intact masses of CCA-tailed, CC-tailed and C-tailed tRNA sequences with the intact dataset, then sum up the intensity for each catogory, and result in three percentage values, 9%, 70% and 21%.

## preparing the data for panel e
We get tRNA-Trp-BCA if matches the Amino-Acid-tailed tRNA sequences with the intact dataset; moreover, we get 8 more tRNAs if match with the acid-degraded dataset. They are Glu-3UC, Leu-CAA, Lys-3UU, Lys-CUU, Pro-UGG, Ser-GCU, Thr-IGU, and Val-CAC.

## preparing the data for panel f
We choose the second acid degraded sample (which has the most abundance fragments) to do the analysis. 
1. Use a sliding window to iterate along the mass values, inside each window, choose 10 fragments with the highest intensity.
2. Collect all the fragments chosen from each window.
3. observe the strongest intact mass, which is 23904.22.
4. Do the MassSum on the selected fragments from step 2, for the intact mass 23904.22.
5. do the base-calling on the result of step 4.

## preparing the data for panel g
With the de-novo sequencing result of panel f, if we do BLAST with the reference, we will get a perfect match with tRNA-AspGUC, on not only the nucleotides but also their precise positions.

## preparing the data for panel h

### how we confirm the nucletides?

1. For each tRNA sequence in the reference, we calculate the mass ladder fragments in silico, and result in 4 different mass ladders: 5´, 3´ CCA-tailed, 3´ CC-tailed, and 3´ C-tailed. Basically, each nuclotide is represented by 4 different masses.
2. Match all the mass ladders with acid degraded sample. As long as the nucletide can match any mass ladder, we confirm that the nucleotide exist inside the acid degraded sample.

### how we confirm the nucletide modifications?
We use exactly the same method as as we do for nucletides.

### how we confirm the partial methylations?
The method we used to confirm the partial modifications for panel h, is different from the one we used for panel c. Panel c presents the partial methylations we detected from intact sample, but panel h is about acid degraded sample.
1. For each tRNA sequence in the reference, we calculate the mass ladder fragments in silico, and result in 4 different mass ladders: 5´, 3´ CCA-tailed, 3´ CC-tailed, and 3´ C-tailed.
2. For each mass ladder, we generate another mass ladder with a mass value shift of -14.01 Da.
3. Match two parallel mass ladders with any acid degraded sample, if we observed both ladders match with a specific methylated nucleotide, and that nucletide is at the leading position of the match, we mark it as a partial methylation.

- acid degraded sample 1

| id | tRNA | Position | Partial Methylation | Mass1 | Vol1 | Mass2 | Vol2 | Ratio | 
| ----| ---- | ---- | ----- | ------- | ------- | ------- | ------- | ------- |
| 4 | ArgICG | 58   |  "	| 5517.763140 | 154842.53 | 5531.805918	| 79194.96 | 33.8% |
| 5 | AsnGUU | 10   |  L	| 3318.408251 | 6589.80 | 3332.420555	| 12499.15 | 65.5% |
| 9 | GlyGCC | 9   |  K	| 3066.406069 | 43454.80 | 3080.419247	| 490466.67 | 91.9% |
| 14 | IleIAU | 9 |  K	| 2967.320687 | 2576.89 | 2981.329880	| 98929.42 | 97.5% |
| 22 | LysCUU | 9   |  L	| 2967.320687 | 2576.89 | 2981.329880	| 98929.42 | 97.5% |
| 25 | MetCAU | 10   |  L	| 3319.392144 | 1580877.15 | 3333.417099	| 67975.47 | 4.1% |
| 27 | Phe#AA  | 10   |  L	| 3358.411861 | 65431.02 | 3372.441115	| 1096.87 | 1.6% |
| 41 | Val&AC | 10   |  L	| 3358.411861 | 65431.02 | 3372.441115	| 1096.87 | 1.6% |
| 42 | ValCAC | 10   |  L	| 3303.395991 | 222967.96 | 3317.408510	| 8454.69 | 3.7% |
| 44 | IlePAP | 10   |  L	| 3335.399032 | 9810.08 | 3349.399471	| 65134.45 | 86.9% |
| 4 | ArgICG | 58   |  "	| 5517.763140 | 154842.53 | 5531.805918	| 79194.96 | 33.8% |


- acid degraded sample 4

| id | tRNA | Position | Partial Methylation | Mass1 | Vol1 | Mass2 | Vol2 | Ratio | 
| ----| ---- | ---- | ----- | ------- | ------- | ------- | ------- | ------- |
| 28 | ProUGG  | 53   |  T	| 6567.853756 | 516603.52 | 6581.91026	| 10007.52 | 1.9% |
| 38 | TrpBCA  | 9   |  K	| 3092.409352 | 14144.90 | 3106.42307	| 4036.88 | 22.2% |
| 43 | ValIAC  | 59   |  ?	| 8591.166609 | 6712.34 | 8605.229679	| 28666.03 | 81.0% |
| 43 | ValIAC  | 59   |  "	| 5406.812447 | 102344.70 | 5420.739182	| 568398.81 | 84.7% |
