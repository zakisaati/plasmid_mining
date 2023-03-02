### Plasmids annotation

The gene calling was done through [prokka](https://github.com/tseemann/prokka) using the following command:

~~~
$ for file in *.fasta
do sample=${file%%.fasta}
echo "prokka --outdir ${sample} --centre X --cpus 0 --prefix ${sample} ${file}"
done > prokka_commands.sh
~~~
~~~
$ bash prokka_commands.sh
~~~
---------

### Search for Biosynthetic Gene Clusters (BGCs) related with the production of Specialized Metabolites

[antiSMASH](https://docs.antismash.secondarymetabolites.org/install/) was used to search for putative BGCs in each of the plasmids. To do so, I used as input each of the annotated gbk files from the previous prokka annotation.

~~~
$ mkdir gbk_files
~~~
~~~
$ mv */*.gbk gbk_files
~~~
~~~
$ cd gbk_files
~~~
~~~
$ conda activate antismash
~~~
~~~
$ for file in *.gbk
do
sample=${file%%.gbk}
echo "antismash --fullhmmer --clusterhmmer --tigrfam --asf  --cb-general --cb-subclusters --cb-knownclusters --pfam2go --rre --smcog-trees --output-dir ${sample}_antismash ${file}"
done > antismash_commands.sh
~~~
~~~
$ bash antismash_commands.sh
~~~

---------

### Analysis of BGCs diversity

Then, the similarity among predicted BGCs was calculated with [BiG-SCAPE](https://bigscape-corason.secondarymetabolites.org/). We included a search for similar BGCs within the [MiBIG](https://mibig.secondarymetabolites.org/) database. The input for this analysis consist on a folder ("BGCs/") containing each single BGC region in gbk format (-> these files are within the antiSMASH output folders)
~~~
$ mkdir BGCs
~~~
~~~
$ cp *_antismash/*region*.gbk BGCs/
~~~
~~~
$ cd BiG-SCAPE-1.1.5
~~~
~~~
$ conda activate  bigscape      
$ python bigscape.py  -i ../plasmid_fasta/gbk_files/BGCs/ -o ../bigscape_output --mode auto --mibig --mix
~~~
