# Performance comparison of two RNA sequencing techniques: DriverMap vs RNAseq

This is a very simplified version of an analysis of an RNA sequencing technique performance, done as a project for the Data Analytics bootcamp from UC Berkeley. We took some liberties (because of lack of time) to avoid some required data manipulation.

The goal of this project was to evaluate the performance of a new RNA sequencing technique called DriverMap, by comparing its overall ability to pick up genes with different levels of expression with an already existing technique, and also to calculate how good the technique is at picking up highly expressing genes.

We received 4 csv files from employer. They comprise datasets with results of RNA sequencing, for two different techniques: RNAseq and DriverMap (DM), using 10 different libraries of primers. Two datasets have the count of reads for each of 19k genes, as a result of aligning the sequence obtained by the sequencing techniques to a database of genes. That alignment was further manipulated to get to the count of reads, which is a measure of how much that gene is expressing in that particular tissue. The other two csv files contain the number of transcripts per millon kilobases of DNA (TPM), which is a normalized measure that makes comparison between samples possible. With these 2 datasets we calculated the log base 2 of TPM counts, to further analyze the difference between techniques in a simpler way (this is ussualy done with biological data).

We investigated how well DM was at picking up genes by doing the following plots:

- We did a heatmap for both techniques and for the whole 19k set of genes to see if there was some obvious difference.
- We then did log2-log2 scatter plots to see correlation between both techniques, and calculated the Pearson correlation coefficient for each pair of libraries.
- To further visualize the density of points in the dataset, we did a KDE plot.
- We then did boxplots of each pair of libraries and techniques, and calculated the difference using a t-test.

We wanted to focus on the high expression genes and compare how the two techniques worked. In order to do this, we binned in the data into no-read genes, low, medium and high expression ones, using the mean+stdev as cut off point for the high expression genes. We visualized the difference by doing:
- Heatmaps for the bins.
- Bar plots of each pair of libraries and techniques.
- Bar plot of percentage of difference in the number of genes picked up by each technique, and calculating the difference with a chi square test.
- Bar plots of means of the difference between TPMs for each library.

Our results show:

1- Both techniques follow the same pattern of high count of no read genes and low expression genes. Both techniques pick up few high expressing genes. Their pattern shows correlation not high enough to say they are replicates.
2-  This is further confirmed by seeing that both techniques show significant difference in their mean of TPM. We can say they are different (not working as replicates).
3- DM looks better at picking up high expressing genes, but it does it at less counts per gene than RNAseq in 5 of the 10 libraries. It would depend on the aim of the study for  what technique to choose.
4- The difference in high expressing genes picked up is always more than 50 percent, and the difference in TPMs between both techniques is significant.

We conclude that DM technique is equivalent and even better than RNAseq, but only for some sets of genes (low expressing and high expressing). If we were required to choose one of the two, it would be important to think about the goal of the study that we wanted to do to pick one.
