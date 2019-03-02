### ReFraction: A machine learning approach for deterministic identification of protein homologs and splice variants in large-scale MS-based proteomics

#### When is ReFraction applicable?

ReFraction is applicable when SDS-PAGE is used for protein separation prior to tryptic digestion.


#### Installation and example

Install ReFraction as below:

```r
devtools::install_github("PengyiYang/ReFraction")
```


#### Example (example dataset are included in the 'data' folder)

Step 1. Read in peptide table. Note that the peptide table should contain "Slice" information from your SDS-PAGE. This should be
denoted as "Slice.1	Slice.2	...".
```r
library(ReFraction)
peptide.tab <- read.delim("data/Maxquant_peptide_table.txt")
peptide.tab[1:2,]
```

Step2. Read in protein database information. This table contains protein features extracted from the protein database you used for searching the peptides in Maxquant.
Note that you need to create this database. See function "extractDatabase.R" for details on how to create this database.
```r 
protein.tab <- read.delim("data/Protein_info_table.txt")
protein.tab[1:2,]
```

Step 3. Apply ReFraction. The code below save the results in the object "output".
```r
output <- applyReFraction(protein.database = protein.tab, peptide.table = peptide.tab, fdr=0.01)

# output protein that are deterministic
output$deterministic.protein.table[1:2,]

# output peptide assignment after applying ReFraction
output$peptide.ReFraction.table[1:2,]
```