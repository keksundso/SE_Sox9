# Superenhacner (SE) and Sox9 overlap.

## Method
Sox9 peaks (GEO; GSM1692996 {Ohba, 2015}) within the same genomic region (200 bp) of SEs were defined as co-localization using StrandNGS (StrandLifeScience, version 2.9). To analyze the enrichment of Sox9 peaks in SEs, the likelihood of an overlap (Y) was compared to that of random shuffled genomic sequences of the same length (bedtools 2.26.0 {Hung, 2017}). As an additional control, the Sox9 peaks where shuffled and the process was repeated. With this data, the following binomial regression model was fitted in a Bayesian framework (brms (2.10.0) with default priors {Burkner, 2018}.

    Yt,s ~ binomial(θt,s , Nt)
    θt,s = logistic(αt + βt * St) 

θt,s is the probability for each type t (PC and HC, each original Sox9 peaks and shuffled peaks) that a SE (s = 1) or SE sized peak (s = 0) has a matching Sox9 peak. N is the number of SE peaks and the slope β is the log odds ratio of SE peaks (S = 1) overlapping with Sox9 compared to randomly located genomic regions (S = 0) overlapping with Sox9. The accuracy of the model was tested by a posterior predictive check  


## Prerequisite
### Software 
1. *bedtools* 2.26.0 {Hung, 2017}
2. R-libraries defined in the *SE_SE_overlap.Rmd*. 

### Data
1. Sox9 peaks (GEO; GSM1692996 {Ohba, 2015})
2. [mm10.chrom.sizes](https://hgdownload.soe.ucsc.edu/goldenPath/mm10/bigZips/mm10.chrom.sizes)
3. HC and PC specific SE bed files. (can be requested)
