Here I show the codes and methods used to download a plasmid database matching with those high quality plasmids used in the following [work](https://www.nature.com/articles/s41467-020-17278-2):

Redondo-Salvo, S., Fernández-López, R., Ruiz, R., Vielva, L., de Toro, M., Rocha, E. P., ... & de la Cruz, F. (2020). Pathways for horizontal gene transfer in bacteria revealed by a global map of their plasmids. Nature communications, 11(1), 3602

There, the authors categorized the microbial plasmids within plasmid taxonomic units (PTUs) – clusters of plasmids with high average nucleotide identity –, and assigned them a host range (species, genus, family, order, class or phylum). 

---------
1. Firtsly, I downloaded all the available plasmids within the refseq database: https://ftp.ncbi.nlm.nih.gov/refseq/release/plasmid/

2. To split the files into individual files:
~~~
$ conda activate split-fasta
~~~
~~~
$ for file in *.fna; do sample=${file%%.fna}; mv ${file}  ${sample}.fasta; done
~~~
~~~
$ for file in *.fasta; do splitfasta ${file}; done
~~~

3. In order to rename the files with the accession number, first do:
~~~
grep ">" plasmid.1*split_files/*.fasta > files_1_accessions.txt
grep ">" plasmid.2*split_files/*.fasta > files_2_accessions.txt
grep ">" plasmid.3*split_files/*.fasta > files_3_accessions.txt
grep ">" plasmid.4*split_files/*.fasta > files_4_accessions.txt
grep ">" plasmid.5*split_files/*.fasta > files_5_accessions.txt
cat files_*_accessions.txt > total_files_accessions.txt
~~~

Then, the file "total_files_accessions.txt" can be crossed with those published in the above mentioned [paper](https://www.nature.com/articles/s41467-020-17278-2). The matching files can be easily copied or moved to the desired location. E.g:
~~~
$ mkdir plasmid_fasta
~~~
~~~
$ mv plasmid.1.1.genomic_split_files/plasmid.1.1.genomic_22077.fasta plasmid_fasta/NC_021737.1.fasta
~~~
