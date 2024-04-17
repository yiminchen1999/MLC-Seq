## samples

### intact samples
https://github.com/rnamodifications/MLC-Seq/tree/main/samples/total_tRNA/Control

### acid degraded samples
https://github.com/rnamodifications/MLC-Seq/tree/main/samples/total_tRNA/AcidDeg

## preprocessing the datasets
Different datesets come with different intensity scales. We align them to the strongest one. Here are the steps:
1. for each dataset, get the strongest intensity from the intact mass area (with mass greater then 23000 Da). 
2. choose the top one among those strongest intensities.
3. compare to the top intensity, we can calculate the calibrate ratio for each dataset.
4. apply the calibrate ratio of each dataset to all the data fragments inside that particular dataset.
5. combine the calibrated datasets.
6. drop duplicated fragments based on the following rules.
    - round the masses of all fragments to integers.
    - put the identical masses into the same group. 
    - inside each group, keep the fragment with the highest intensity only. The rest in the group were treated as duplicated ones, remove them.

## tRNA reference
we use Yeast tRNAs sequences retrieved from the database:
https://tpsic.igcz.poznan.pl/info/start/

## preparing the data for panel a
1. calculate the theoretical monoisotopic mass for each sequence, and the ones for their Amino-Acid-tailed, CC-tailed, C-tailed isoforms as well. Basically, we have 4 monoisotopic masses for each tRNA sequence.
2. match the theoretical monoisotopic masses with the dataset of intact samples (all the fragments with masses greater than 23000 Da), find out the matched ones. We use 10 PPM as the cutoff, for example, if the masses of two fragments (one from the theoretical masses list, and the other from the sample's intact dataset) are close enough, in other words, their PPM is within 10, then we can say that the fragment from the dataset is matched with the theoretical mass of a particular tRNA sequence.

## preparing the data for panel b
based on the matched fragments from panel a, we do the following steps:
1. to avoid a messy figure, we use 1E6 as a cutoff to filter the matched fragments by intensity.
2. we get all the fragment pairs which have a mass difference equals to nucletide A or C, that's 329.05 Da and 305.04 Da respectively.

## preparing the data for panel c
based on the matched fragments from panel a, compare the masses of fragments with ones in the intact sample, if we observed a pair of masses which has a mass difference equals to a methylation, 14.01 Da, we can say that these two fragments might be the partial methylation.

## preparing the data for panel d
we match the intact masses of CCA-tailed, CC-tailed and C-tailed tRNA sequences with the intact dataset, then sum up the intensity for each catogory, and result in three percentage values, 9%, 70% and 21%.

## preparing the data for panel e
we get tRNA-Trp-BCA if matches the Amino-Acid-tailed tRNA sequences with the intact dataset; moreover, we get 8 more tRNAs if match with the acid-degraded dataset. They are Glu-3UC, Leu-CAA, Lys-3UU, Lys-CUU, Pro-UGG, Ser-GCU, Thr-IGU, and Val-CAC.

