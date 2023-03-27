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
