# BIOL 738 Collaborative Project
Hello! This repository holds information on how to use R and run DGE analysis in R. You can see below for a tutorial on how to use R for a DGE analysis.

# DGE Analysis in R
Working in R starts with downloading R! Download R at https://cran.r-project.org/. Be sure to download the correct version of R for your device. If you are on a Windows device, you can download the base package.

We worked in R through RStudio. Now with R downloaded, you can download and use RStudio at https://docs.posit.co/ide/user/?ref=rstudio-legacy#rstudio-ide-oss-downloads. 

Conducting the DGE analysis in R also requires downloading a dataset with DNA and RNA information from a place like NCBI's GEO database. Make sure that while looking through these data files, you look for supplementary files in .txt format. Be sure that the supplementary file you download is also gene counts and not another type of data. There may be a lot of metadata in your dataset. That is okay, but you will likely need to attend to that later.

From here, you can extrapolate from your dataset and make a .tsv document (via something like Google Sheets) that includes the samples (which you can take from the sample row names in your gene counts datasheet), and what was being tested with those samples.

Finally, you can open up RStudio and begin the Harvard tutorial. The tutorial recites this as well, but you need to download packages before you can get started so you can run the scripts correctly. The packages you need to download are tidyverse, edgeR, limma, and ggrepel. To download tidyverse onto your device, you can use the install.packages tool:

install.packages("tidyverse")

You'll need to install the remaining packages through BiocManager, so the code will look like:

BiocManager::install("limma","edgeR","ggrepel")

You may also need to use BiocManager separately for each of the packages if you receive an error code for trying to download them all at once with BiocManager. The code listed in the tutorial still might not work unless you library the packages. An example of that code would look like:

library("limma")

Doing this function will activate the package despite already having downloaded it. From here, the tutorial can be followed step by step, though you may want to make sure that the metadata in your dataset isn't causing errors down the road. If it does result in errors, you can take off the columns of metadata by nulling various columns of the dataset. What is important to have in your dataset is the gene ID and row names that correspond to your .tsv file that you made earlier on. After you have read your table in R and piped it into expression_data, you can null a column in R by using the format:

expression_data$gene_name=NULL

Another problem that might come about with too much metadata is the data getting hard to read with additional spaces and semicolons. You might need to manually go into the read.table function and specify that a tab is the separator of the columns and specify which characters close text strings. For example:

expression_data <-read.table("GSE319495_gene_count.txt",header=TRUE,row.names="gene_id",sep="\t",quote="")

Once you've cleared up this information, you should be able to run through the Harvard tutorial smoothly! When copying and pasting from the Harvard tutorial, you will need to change the terms used to match the terms that are pertinent to your dataset.

Happy coding!
