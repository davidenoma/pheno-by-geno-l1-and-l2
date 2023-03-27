# pheno-by-geno-l1-and-l2
Predicting phenotype by genotype: a comparison of lasso and ridge regularized regression
# Introduction
The research goal of this study is to model, evaluate and compare the power of machine
learning models to predict the phenotype given the genotype. The models which will be
compared against each other include the polygenetic linear model, L1 (LASSO) regularization
and L2 (Ridge) regularization. (Long et al., 2013) developed a tool called JAWAMix5 which is
used for genome-wide association mapping. The JawaMix5 tool embeds the emmax
function and is well-suited to the format of the input genotype file. The tool will enable the
narrowing down of total SNPs (214,553) to identify the candidate SNPs for evaluating
models.



## Results
The Jawamix5 tool was used to visualize the analytical results and plot—Manhattan plots for
logged P-values. Jawamix5 embeds EMMAX, which takes an expedited mixed linear model
approach to correct for sample structure (Kang et al., 2010). The model has a procedure for
estimating the contribution of the kinship matrix to the phenotypes, whereas the other
methods do not. The number of candidate SNPs was 1256 after the genome-wide
association mapping. We generated a p-value, Adjusted R squared, coefficient and standard
error. However, for the next step, we sorted the SNPs in ascending order from the minimum
p-value. Eventually, the SNPS would compare the lasso and ridge regression.
## Performance of Lasso and Ridge regression with R

![image](https://user-images.githubusercontent.com/24875399/228058771-187aea01-3522-48fa-b661-0d4721c164d1.png)

## Analysis of Top SNPs with GFF model
Furthermore, we analyzed the SNPs set that gave the best predictions and found that more
of the SNPs' features were in the coding region. There were fewer gene artifacts in this
dataset than with the entire output of EMMAX 
![image](https://user-images.githubusercontent.com/24875399/228059095-b3114a90-287a-4766-a05b-6dd194ec9e80.png)


### Study pipeline
![Study pipeline](https://github.com/davidenoma/pheno-by-geno-l1-and-l2/blob/main/PIPELINE.png )

## Quality Control
The pandas package of Python version 3.9 was used for pre-processing the datasets for
input genotype and phenotype files for modelling in Jawamix5.
## Genome-wide association mapping
The input genotype is processed with Jawamix5 to obtain the significant SNPs and their pvalues. The steps taken include generating the recode and converting the genotype recodeto hdf5 (This is done to increase processing speed). Consequently, the other steps involve creating a kinship matrix and the genome-wide linear mixed model regression for the phenotype of interest.
## Regression models
The R programming language was used with packages, readr, tidyverse, and caret glmnet to
model lasso and ridge. After the data preparation of the files for modelling, k-fold crossvalidation with glmnet was done to obtain lambda values for the lasso and ridge regression. Glmnet was also used for modelling the genotype-phenotype relationship. Consequently, the caret package was used for computing the R-squared and MSE values.
## Annotation
The annotation of the top SNPs was done with bash scrips and the bedtools package. This
package enables the processing of the GFF file to obtain features.
## Supplementary information
The additional code has been attached as single python, R, and unix command files

## References

Kang, H. M., Sul, J. H., Service, S. K., Zaitlen, N. A., Kong, S., Freimer, N. B., Sabatti, C., &
Eskin, E. (2010). Variance component model to account for sample structure in
genome-wide association studies. Nature Genetics, 42(4), Article 4.
https://doi.org/10.1038/ng.548

Long, Q., Zhang, Q., Vilhjalmsson, B. J., Forai, P., Seren, Ü., & Nordborg, M. (2013).
JAWAMix5: An out-of-core HDF5-based java implementation of whole-genome association studies using mixed models. Bioinformatics, 29(9), 1220–1222.
https://doi.org/10.1093/bioinformatics/btt122

