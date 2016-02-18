# EST-SSR
**Introduction**
<br>Simple sequence repeat (SSR) can be developed from public sequences data. 
For example, dbEST.

**Objective**
<br>To discover SSR from EST sequences 

**Requirements**
<br>1. vector removal (seqtrim.pl)
<br>2. sequence trimming (est_trimmer.pl)
<br>3. sequence assembly (cap3)
<br>4. SSR discovery (misa.pl, misa.ini)
<br>5. SSR filtering (R & Perl)

**Instructions/Steps**
<br>1. Checking all the scripts and tools

**A. Pre processing**
<br>2. Remove vector using seqtrim.pl
       perl seqtrim.pl -a v -f  <input file est sequences.fa> -o <output file>
       #remember to check sequence without vector trimming
<br>3. Trimming poly A-tail using est_trimmer.pl
       perl est_trimmer.pl ESTs.fasta -amb=2,50 -tr5=T,5,50 -tr3=A,5,50 -cut=100,700

**B. Sequence assembly**
<br>4. Assemble using cap3
       ./cap3 ananas.fasta -p 90 -o 50
<br>5. create contigs & singlet in single file
       mkdir unigenes.fasta cat singlet.fasta contigs.fasta > unigene.fasta

**C. Mining SSR**
<br>6. Prepare file misa.ini. Save as misa.ini
       <br>definition(unit_size,min_repeats):                   1-10 2-6 3-5 4-5 5-5 6-5
       <br>interruptions(max_difference_between_2_SSRs):        100
<br>7. Run script ‘misa.pl’
       perl misa.pl unigenes.fa

