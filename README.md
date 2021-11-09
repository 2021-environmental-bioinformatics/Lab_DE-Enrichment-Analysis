# Lab_DE-Enrichment-Analysis

Get set up: copy the `DE_results.csv` you just created into this repo.

A lot of downstream file processing involves getting files into slightly different formats, and enrichment analysis is no exception, so this is more of a series of exercises in data-wrangling than a "cookbook" set of directions.

I've provided you with a file called `Rh_NC_sal_txm-all-noContam_GO-terms.tab` that "maps" each contig to a list of GO terms. Contigs that couldn't be annotated are listed as "unknown". What percentage of contigs are annotated in this transcriptome assembly?

Find all contigs with padj < 0.05, and put the contig names into a new file called `DE_res_p05.txt`. (Use bash, python, or R - your choice!)

Now, select only the lines in `Rh_NC_sal_txm-all-noContam_GO-terms.tab` that correspond to the contigs with significantly different expression, and move only the GO terms to a new file called `DE_res_p05_GO.txt`. Modify that file so that one GO term is on each line, and remove the unannotated contigs. (Use bash, python, or R - your choice! Feel free to mix and match and use Notepad or another text editor and regex, if it helps.)

This one we'll give you some help on - you can read in the list of contig names in bash, and work with each line in a loop using a structure like this:

```
while read line
do
 echo $line
done < \[INFILE_NAME\] 
```

...and another nice trick, the `tr` ("transform") command, which can swap one character for another - for example, newlines for semicolons:

```
tr ';' '\n' < INFILE > OUTFILE 
```

Now we should have a nice list of GO terms corresponding to (annotated) contigs with significantly different expression. What are they doing? As we've discussed in lecture, there are several ways to look at this. Here, we're just going to explore a little with an online visualization tool called Revigo. (http://revigo.irb.hr/) Surf on over, copy and paste your list of GO terms, and use the visual interface to explore the functional categories they cluster into.
