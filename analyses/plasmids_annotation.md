# Plasmids annotation
for file in *.fasta; do sample=${file%%.fasta}; echo "prokka --outdir ${sample} --centre X --cpus 0 --prefix ${sample} ${file}"; echo "rm ${sample}/${sample}.err ${sample}/${sample}.ffn ${sample}/${sample}.fsa ${sample}/${sample}.log ${sample}/${sample}.sqn ${sample}/${sample}.tbl ${sample}/${sample}.txt ${sample}/${sample}.fna"; echo "gzip ${sample}.gff"; done > prokka_commands.sh

---------

# Search for Biosynthetic Gene Clusters (BGCs) related with the production of Specialized Metabolites

~~~
$ mkdir gbk_files
~~~
~~~
$ mv */*.gbk gbk_files
~~~
~~~
$ cd gbk_files
~~~
c conda activate antismash
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

# Analysis of BGCs diversity

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
