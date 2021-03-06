KHMER=/usr/local/src/khmer

# khmer paper pipeline
# raw data:
#	iowa_prairie_0920.fa.1
#	iowa_prairie_0920.fa.2
#	iowa_prairie_0920.fa.3
#	iowa_prairie_0920.fa.4
#	iowa_prairie_0920.fa.5
#	MH0001.trimmed.fa
#	ecoli_ref.fastq

all: benchmark jellyfish tallymer dsk check_fp_rate check_error abundance_filtering counts

copydata:
	rm -fr ../data/
	mkdir ../data/
	cp jelly_*_22.hist *.time* ecoli_ref.fastq.pos*.abund1 fp_assessment.out *.wc ../data/


clean:
	rm -f `cat clean-list.txt`

counts: bloom_1_1_22.count.time bloom_2_1_22.count.time bloom_3_1_22.count.time bloom_4_1_22.count.time bloom_5_1_22.count.time jelly_1_22.count.time jelly_2_22.count.time jelly_3_22.count.time jelly_4_22.count.time jelly_5_22.count.time 1_part1_22.count.time 2_part1_22.count.time 3_part1_22.count.time 4_part1_22.count.time 5_part1_22.count.time

benchmark: bloom_1_1_22.hist bloom_2_1_22.hist bloom_3_1_22.hist bloom_4_1_22.hist bloom_5_1_22.hist \
    bloom_1_5_22.hist bloom_2_5_22.hist bloom_3_5_22.hist bloom_4_5_22.hist bloom_5_5_22.hist

kmerlist2.fa:
	cut -c 1-22 iowa_prairie_0920.fa.1 > kmerlist2.fa

kmerlist2: kmerlist2.fa
	grep -v ^'>' kmerlist2.fa > kmerlist2

bloom_1_1_22.hist:
	time -o bloom_1_1_22.time1 abundance-dist-inmem.py --threads 8 --ksize 22 --n_hashes 4 --hashsize 1476277798 --threads 8 -s iowa_prairie_0920.fa.1 bloom_1_1_22.hist

bloom_1_1_22.kh:
	time -o bloom_1_1_22.time2 load-into-counting.py --ksize 22 --n_hashes 4 --hashsize 1476277798 --threads 8 bloom_1_1_22.kh iowa_prairie_0920.fa.1

bloom_1_1_22.count.time: bloom_1_1_22.kh kmerlist2
	time -o bloom_1_1_22.count.time python khmer-count-kmers.py bloom_1_1_22.kh kmerlist2

bloom_2_1_22.hist:
	time -o bloom_2_1_22.time1 abundance-dist-inmem.py --threads 8 --ksize 22 --n_hashes 4 --hashsize 2789448361 --threads 8 -s iowa_prairie_0920.fa.2 bloom_2_1_22.hist

bloom_2_1_22.kh:
	time -o bloom_2_1_22.time2 load-into-counting.py --ksize 22 --n_hashes 4 --hashsize 2789448361 --threads 8 bloom_2_1_22.kh iowa_prairie_0920.fa.2

bloom_2_1_22.count.time: bloom_2_1_22.kh kmerlist2
	time -o bloom_2_1_22.count.time python khmer-count-kmers.py bloom_2_1_22.kh kmerlist2

bloom_3_1_22.hist:
	time -o bloom_3_1_22.time1 abundance-dist-inmem.py --threads 8 --ksize 22 --n_hashes 4 --hashsize 3803756180 --threads 8 -s iowa_prairie_0920.fa.3 bloom_3_1_22.hist

bloom_3_1_22.kh:
	time -o bloom_3_1_22.time2 load-into-counting.py --ksize 22 --n_hashes 4 --hashsize 3803756180 --threads 8 bloom_3_1_22.kh iowa_prairie_0920.fa.3

bloom_3_1_22.count.time: bloom_3_1_22.kh kmerlist2
	time -o bloom_3_1_22.count.time python khmer-count-kmers.py bloom_3_1_22.kh kmerlist2

bloom_4_1_22.hist:
	time -o bloom_4_1_22.time1 abundance-dist-inmem.py --threads 8 --ksize 22 --n_hashes 4 --hashsize 4657846829 --threads 8 -s iowa_prairie_0920.fa.4 bloom_4_1_22.hist

bloom_4_1_22.kh:
	time -o bloom_4_1_22.time2 load-into-counting.py --ksize 22 --n_hashes 4 --hashsize 4657846829 --threads 8 bloom_4_1_22.kh iowa_prairie_0920.fa.4

bloom_4_1_22.count.time: bloom_4_1_22.kh kmerlist2
	time -o bloom_4_1_22.count.time python khmer-count-kmers.py bloom_4_1_22.kh kmerlist2

bloom_5_1_22.hist:
	time -o bloom_5_1_22.time1 abundance-dist-inmem.py --threads 8 --ksize 22 --n_hashes 4 --hashsize 5580911687 --threads 8 -s iowa_prairie_0920.fa.5 bloom_5_1_22.hist

bloom_5_1_22.kh:
	time -o bloom_5_1_22.time2 load-into-counting.py --ksize 22 --n_hashes 4 --hashsize 5580911687 --threads 8 bloom_5_1_22.kh iowa_prairie_0920.fa.5

bloom_5_1_22.count.time: bloom_5_1_22.kh kmerlist2
	time -o bloom_5_1_22.count.time python khmer-count-kmers.py bloom_5_1_22.kh kmerlist2

bloom_1_5_22.hist:
	time -o bloom_1_5_22.time1 abundance-dist-inmem.py --threads 8 --ksize 22 --n_hashes 4 --hashsize 876416775 --threads 8 -s iowa_prairie_0920.fa.1 bloom_1_5_22.hist

bloom_1_5_22.kh:
	time -o bloom_1_5_22.time2 load-into-counting.py --ksize 22 --n_hashes 4 --hashsize 876416775 --threads 8 bloom_1_5_22.kh iowa_prairie_0920.fa.1

bloom_2_5_22.hist:
	time -o bloom_2_5_22.time1 abundance-dist-inmem.py --threads 8 --ksize 22 --n_hashes 4 --hashsize 1656002238 --threads 8 -s iowa_prairie_0920.fa.2 bloom_2_5_22.hist

bloom_2_5_22.kh:
	time -o bloom_2_5_22.time2 load-into-counting.py --ksize 22 --n_hashes 4 --hashsize 1656002238 --threads 8 bloom_2_5_22.kh iowa_prairie_0920.fa.2

bloom_3_5_22.hist:
	time -o bloom_3_5_22.time1 abundance-dist-inmem.py --threads 8 --ksize 22 --n_hashes 4 --hashsize 2258162881 --threads 8 -s iowa_prairie_0920.fa.3 bloom_3_5_22.hist

bloom_3_5_22.kh:
	time -o bloom_3_5_22.time2 load-into-counting.py --ksize 22 --n_hashes 4 --hashsize 2258162881 --threads 8 bloom_3_5_22.kh iowa_prairie_0920.fa.3

bloom_4_5_22.hist:
	time -o bloom_4_5_22.time1 abundance-dist-inmem.py --threads 8 --threads 8 --ksize 22 --n_hashes 4 --hashsize 2765207947 --threads 8 -s iowa_prairie_0920.fa.4 bloom_4_5_22.hist

bloom_4_5_22.kh:
	time -o bloom_4_5_22.time2 load-into-counting.py --ksize 22 --n_hashes 4 --hashsize 2765207947 --threads 8 bloom_4_5_22.kh iowa_prairie_0920.fa.4

bloom_5_5_22.hist:
	time -o bloom_5_5_22.time1 abundance-dist-inmem.py --threads 8 --ksize 22 --n_hashes 4 --hashsize 3313200694 --threads 8 -s iowa_prairie_0920.fa.5 bloom_5_5_22.hist

bloom_5_5_22.kh:
	time -o bloom_5_5_22.time2 load-into-counting.py --ksize 22 --n_hashes 4 --hashsize 3313200694 --threads 8 bloom_5_5_22.kh iowa_prairie_0920.fa.5

jellyfish: jelly_1_22.hist jelly_2_22.hist jelly_3_22.hist jelly_4_22.hist jelly_5_22.hist\
    jelly_1_31.hist jelly_2_31.hist jelly_3_31.hist jelly_4_31.hist jelly_5_31.hist
	# Jellyfish benchmark k=22 and k=31

jelly_1_22.hist:
	time -o jelly_1_22.time1 jellyfish count -m 22 -c 2 -C -s 701472602 -t 8 -o jelly_1_22 iowa_prairie_0920.fa.1
	time -o jelly_1_22.time2 jellyfish histo -t 8 -o jelly_1_22.hist ./jelly_1_22_0

jelly_1_22.count.time: jelly_1_22.hist kmerlist2
	time -o jelly_1_22.count.time bash jelly-search.sh jelly_1_22_0 kmerlist2

jelly_2_22.count.time: jelly_2_22.hist kmerlist2
	time -o jelly_2_22.count.time bash jelly-search.sh jelly_2_22_0 kmerlist2

jelly_3_22.count.time: jelly_3_22.hist kmerlist2
	time -o jelly_3_22.count.time bash jelly-search.sh jelly_3_22_0 kmerlist2


jelly_4_22.count.time: jelly_4_22.hist kmerlist2
	time -o jelly_4_22.count.time bash jelly-search.sh jelly_4_22_0 kmerlist2

jelly_2_22.hist:
	time -o jelly_2_22.time1 jellyfish count -m 22 -c 2 -C -s 1325442680 -t 8 -o jelly_2_22 iowa_prairie_0920.fa.2
	time -o jelly_2_22.time2 jellyfish histo -t 8 -o jelly_2_22.hist ./jelly_2_22_0

jelly_3_22.hist:
	time -o jelly_3_22.time1 jellyfish count -m 22 -c 2 -C -s 1807404236 -t 8 -o jelly_3_22 iowa_prairie_0920.fa.3
	time -o jelly_3_22.time2 jellyfish histo -t 8 -o jelly_3_22.hist ./jelly_3_22_0

jelly_4_22.hist:
	time -o jelly_4_22.time1 jellyfish count -m 22 -c 2 -C -s 2213236520 -t 8 -o jelly_4_22 iowa_prairie_0920.fa.4
	time -o jelly_4_22.time2 jellyfish histo -t 8 -o jelly_4_22.hist ./jelly_4_22_0

jelly_5_22.hist:
	time -o jelly_5_22.time1 jellyfish count -m 22 -c 2 -C -s 2651842796 -t 8 -o jelly_5_22 iowa_prairie_0920.fa.5
	time -o jelly_5_22.time2 jellyfish histo -t 8 -o jelly_5_22.hist ./jelly_5_22_0

jelly_5_22.count.time: jelly_5_22.hist kmerlist2
	time -o jelly_5_22.count.time bash jelly-search.sh jelly_5_22_0 kmerlist2

jelly_1_31.hist:
	time -o jelly_1_31.time1 jellyfish count -m 31 -c 2 -C -s 701472602 -t 8 -o jelly_1_31 iowa_prairie_0920.fa.1
	time -o jelly_1_31.time2 jellyfish histo -t 8 -o jelly_1_31.hist ./jelly_1_31_0

jelly_2_31.hist:
	time -o jelly_2_31.time1 jellyfish count -m 31 -c 2 -C -s 1325442680 -t 8 -o jelly_2_31 iowa_prairie_0920.fa.2
	time -o jelly_2_31.time2 jellyfish histo -t 8 -o jelly_2_31.hist ./jelly_2_31_0

jelly_3_31.hist:
	time -o jelly_3_31.time1 jellyfish count -m 31 -c 2 -C -s 1807404236 -t 8 -o jelly_3_31 iowa_prairie_0920.fa.3
	time -o jelly_3_31.time2 jellyfish histo -t 8 -o jelly_3_31.hist ./jelly_3_31_0

jelly_4_31.hist:
	time -o jelly_4_31.time1 jellyfish count -m 31 -c 2 -C -s 2213236520 -t 8 -o jelly_4_31 iowa_prairie_0920.fa.4
	time -o jelly_4_31.time2 jellyfish histo -t 8 -o jelly_4_31.hist ./jelly_4_31_0

jelly_5_31.hist:
	time -o jelly_5_31.time1 jellyfish count -m 31 -c 2 -C -s 2651842796 -t 8 -o jelly_5_31 iowa_prairie_0920.fa.5
	time -o jelly_5_31.time2 jellyfish histo -t 8 -o jelly_5_31.hist ./jelly_5_31_0

	# Tallymer benchmark part=1,k =22
tallymer: 1_part1_22.hist 2_part1_22.hist 3_part1_22.hist 4_part1_22.hist 5_part1_22.hist

1_part1_22.hist:
	time -o suffix_1_part1.time gt suffixerator -dna -pl -tis -suf -lcp -db iowa_prairie_0920.fa.1 -indexname 1_part1
	time -o mkindex_1_part1_22.time gt tallymer mkindex -mersize 22  -esa 1_part1 >1_part1_22.hist

1_part1.mct: 1_part1_22.hist
	gt tallymer mkindex -mersize 22 -esa 1_part1 -counts -pl 8 -indexname 1_part1 -minocc 1

1_part1_22.count.time: 1_part1.mct kmerlist2.fa
	time -o 1_part1_22.count.time bash tallymer-search.sh 1_part1 kmerlist2.fa

2_part1_22.hist:
	time -o suffix_2_part1.time gt suffixerator -dna -pl -tis -suf -lcp -db iowa_prairie_0920.fa.2 -indexname 2_part1
	time -o mkindex_2_part1_22.time gt tallymer mkindex -mersize 22  -esa 2_part1 >2_part1_22.hist

2_part1.mct: 2_part1_22.hist
	gt tallymer mkindex -mersize 22 -esa 2_part1 -counts -pl 8 -indexname 2_part1 -minocc 1

2_part1_22.count.time: 2_part1.mct kmerlist2.fa
	time -o 2_part1_22.count.time bash tallymer-search.sh 2_part1 kmerlist2.fa

3_part1_22.hist:
	time -o suffix_3_part1.time gt suffixerator -dna -pl -tis -suf -lcp -db iowa_prairie_0920.fa.3 -indexname 3_part1
	time -o mkindex_3_part1_22.time gt tallymer mkindex -mersize 22  -esa 3_part1 >3_part1_22.hist

3_part1.mct: 3_part1_22.hist
	gt tallymer mkindex -mersize 22 -esa 3_part1 -counts -pl 8 -indexname 3_part1 -minocc 1

3_part1_22.count.time: 3_part1.mct kmerlist2.fa
	time -o 3_part1_22.count.time bash tallymer-search.sh 3_part1 kmerlist2.fa

4_part1_22.hist:
	time -o suffix_4_part1.time gt suffixerator -dna -pl -tis -suf -lcp -db iowa_prairie_0920.fa.4 -indexname 4_part1
	time -o mkindex_4_part1_22.time gt tallymer mkindex -mersize 22  -esa 4_part1 >4_part1_22.hist

4_part1.mct: 4_part1_22.hist
	gt tallymer mkindex -mersize 22 -esa 4_part1 -counts -pl 8 -indexname 4_part1 -minocc 1

4_part1_22.count.time: 4_part1.mct kmerlist2.fa
	time -o 4_part1_22.count.time bash tallymer-search.sh 4_part1 kmerlist2.fa

5_part1_22.hist:
	time -o suffix_5_part1.time gt suffixerator -dna -pl -tis -suf -lcp -db iowa_prairie_0920.fa.5 -indexname 5_part1
	time -o mkindex_5_part1_22.time gt tallymer mkindex -mersize 22  -esa 5_part1 >5_part1_22.hist

5_part1.mct: 5_part1_22.hist
	gt tallymer mkindex -mersize 22 -esa 5_part1 -counts -pl 8 -indexname 5_part1 -minocc 1

5_part1_22.count.time: 5_part1.mct kmerlist2.fa
	time -o 5_part1_22.count.time bash tallymer-search.sh 5_part1 kmerlist2.fa


dsk: dsk_1_22.time dsk_2_22.time dsk_3_22.time dsk_4_22.time dsk_5_22.time
	# dsk benchmark k=22
dsk_1_22.time:
	time -o dsk_1_22.time dsk iowa_prairie_0920.fa.1 22 -histo

dsk_2_22.time:
	time -o dsk_2_22.time dsk iowa_prairie_0920.fa.2 22 -histo

dsk_3_22.time:
	time -o dsk_3_22.time dsk iowa_prairie_0920.fa.3 22 -histo

dsk_4_22.time:
	time -o dsk_4_22.time dsk iowa_prairie_0920.fa.4 22 -histo

dsk_5_22.time:
	time -o dsk_5_22.time dsk iowa_prairie_0920.fa.5 22 -histo


check_fp_rate: fp_assessment.out
	# Assessment of false positive rate and miscount distribution

random_kmers_1M_3c.fa:
	python get_random_kmers_1M_C3.py >random_kmers_1M_3c.fa

	# get random reads with the same number of unique k-mers 
random_reads_1.67M_3c_0.03e.fa:
	python simulate_random_reads.py 1670000 3 0.03 44 random_reads_1.67M_3c_0.03e.fa random_genome_1M.fa

random_reads_2.54M_3c_0.00e.fa:
	python simulate_random_reads.py 2540000 3 0.00 44 random_reads_2.54M_3c_0.00e.fa random_genome_1M.fa

MH0001.trimmed.head176800.fa:
	head -176800 MH0001.trimmed.fa >MH0001.trimmed.head176800.fa

fp_assessment.out: random_kmers_1M_3c.fa random_reads_1.67M_3c_0.03e.fa random_reads_2.54M_3c_0.00e.fa MH0001.trimmed.head176800.fa
	python fp_assessment.py fp_assessment.out

check_error: ecoli_ref.fastq.pos17.abund1 ecoli_ref.fastq.pos32.abund1
# Investigation of sequencing error pattern by k-mer abundance distribution
# raw data:ecoli_ref.fastq

ecoli_ref.fastq.ht.k17: ecoli_ref.fastq
	load-into-counting.py --ksize 17 --n_hashes 4 --hashsize 1e9 ecoli_ref.fastq.ht.k17 ecoli_ref.fastq


ecoli_ref.fastq.pos17.abund1: ecoli_ref.fastq.ht.k17 ecoli_ref.fastq
	python ${KHMER}/sandbox/hi-lo-abundance-by-position.py ecoli_ref.fastq.ht.k17 ecoli_ref.fastq
	mv ecoli_ref.fastq.pos.abund\=1 ecoli_ref.fastq.pos17.abund1

ecoli_ref.fastq.ht.k32: ecoli_ref.fastq
	load-into-counting.py --ksize 32 --n_hashes 4 --hashsize 1e9 ecoli_ref.fastq.ht.k32 ecoli_ref.fastq

ecoli_ref.fastq.pos32.abund1: ecoli_ref.fastq.ht.k32 ecoli_ref.fastq
	python ${KHMER}/sandbox/hi-lo-abundance-by-position.py ecoli_ref.fastq.ht.k32 ecoli_ref.fastq
	mv ecoli_ref.fastq.pos.abund\=1 ecoli_ref.fastq.pos32.abund1


abundance_filtering: bad_reads.wc remaining_reads.wc

	# step1 preprocess tallymer database
MH0001-reads.mer:
	gt suffixerator -dna -pl -tis -suf -lcp -v -parts 4 -db MH0001.trimmed.fa -indexname MH0001
	gt tallymer mkindex -mersize 32 -minocc 1 -maxocc 1 -esa MH0001 -indexname MH0001-reads -counts -pl

	# hash table size: 1e10
e10_MH0001.trimmed.fa.abundfilt: MH0001.trimmed.fa
	load-into-counting.py --ksize 32 --n_hashes 4 --hashsize 2000000000 --threads 8 MH0001.trimmed.fa.kh MH0001.trimmed.fa
	filter-abund.py MH0001.trimmed.fa.kh MH0001.trimmed.fa
	mv MH0001.trimmed.fa.abundfilt e10_MH0001.trimmed.fa.abundfilt

e10_MH0001.trimmed.fa.abundfilt.abundfilt: e10_MH0001.trimmed.fa.abundfilt
	load-into-counting.py --ksize 32 --n_hashes 4 --hashsize 2000000000 --threads 8 e10_MH0001.trimmed.fa.abundfilt.kh e10_MH0001.trimmed.fa.abundfilt
	filter-abund.py e10_MH0001.trimmed.fa.abundfilt.kh e10_MH0001.trimmed.fa.abundfilt

e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt: e10_MH0001.trimmed.fa.abundfilt.abundfilt
	load-into-counting.py --ksize 32 --n_hashes 4 --hashsize 2000000000 --threads 8 e10_MH0001.trimmed.fa.abundfilt.abundfilt.kh e10_MH0001.trimmed.fa.abundfilt.abundfilt
	filter-abund.py e10_MH0001.trimmed.fa.abundfilt.abundfilt.kh e10_MH0001.trimmed.fa.abundfilt.abundfilt

e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt: e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt
	load-into-counting.py --ksize 32 --n_hashes 4 --hashsize 2000000000 --threads 8 e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.kh e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt
	filter-abund.py e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.kh e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt

e10_MH0001.trimmed.fa.abundfilt.unique.sequence_id: MH0001-reads.mer e10_MH0001.trimmed.fa.abundfilt
	gt tallymer search -output qseqnum qpos counts -tyr MH0001-reads  -q e10_MH0001.trimmed.fa.abundfilt >e10_MH0001.trimmed.fa.abundfilt.unique
	more e10_MH0001.trimmed.fa.abundfilt.unique |cut -f 1|sort -u >e10_MH0001.trimmed.fa.abundfilt.unique.sequence_id

e10_MH0001.trimmed.fa.abundfilt.abundfilt.unique.sequence_id: MH0001-reads.mer e10_MH0001.trimmed.fa.abundfilt.abundfilt
	gt tallymer search -output qseqnum qpos counts -tyr MH0001-reads  -q e10_MH0001.trimmed.fa.abundfilt.abundfilt >e10_MH0001.trimmed.fa.abundfilt.abundfilt.unique
	more e10_MH0001.trimmed.fa.abundfilt.abundfilt.unique |cut -f 1|sort -u >e10_MH0001.trimmed.fa.abundfilt.abundfilt.unique.sequence_id

e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.unique.sequence_id: MH0001-reads.mer e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt
	gt tallymer search -output qseqnum qpos counts -tyr MH0001-reads  -q e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt >e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.unique
	more e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.unique |cut -f 1|sort -u >e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.unique.sequence_id

e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt.unique.sequence_id: MH0001-reads.mer e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt
	gt tallymer search -output qseqnum qpos counts -tyr MH0001-reads  -q e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt >e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt.unique
	more e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt.unique |cut -f 1|sort -u >e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt.unique.sequence_id

	# hash table size: 1e9
e9_MH0001.trimmed.fa.abundfilt: MH0001.trimmed.fa
	load-into-counting.py --ksize 32 --n_hashes 4 --hashsize 1000000000 --threads 8 MH0001.trimmed.fa.kh MH0001.trimmed.fa
	filter-abund.py MH0001.trimmed.fa.kh MH0001.trimmed.fa
	mv MH0001.trimmed.fa.abundfilt e9_MH0001.trimmed.fa.abundfilt

e9_MH0001.trimmed.fa.abundfilt.abundfilt: e9_MH0001.trimmed.fa.abundfilt
	load-into-counting.py --ksize 32 --n_hashes 4 --hashsize 1000000000 --threads 8 e9_MH0001.trimmed.fa.abundfilt.kh e9_MH0001.trimmed.fa.abundfilt
	filter-abund.py e9_MH0001.trimmed.fa.abundfilt.kh e9_MH0001.trimmed.fa.abundfilt

e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt: e9_MH0001.trimmed.fa.abundfilt.abundfilt
	load-into-counting.py --ksize 32 --n_hashes 4 --hashsize 1000000000 --threads 8 e9_MH0001.trimmed.fa.abundfilt.abundfilt.kh e9_MH0001.trimmed.fa.abundfilt.abundfilt
	filter-abund.py e9_MH0001.trimmed.fa.abundfilt.abundfilt.kh e9_MH0001.trimmed.fa.abundfilt.abundfilt

e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt: e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt
	load-into-counting.py --ksize 32 --n_hashes 4 --hashsize 1000000000 --threads 8 e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.kh e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt
	filter-abund.py e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.kh e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt


e9_MH0001.trimmed.fa.abundfilt.unique.sequence_id: MH0001-reads.mer e9_MH0001.trimmed.fa.abundfilt
	gt tallymer search -output qseqnum qpos counts -tyr MH0001-reads  -q e9_MH0001.trimmed.fa.abundfilt >e9_MH0001.trimmed.fa.abundfilt.unique
	more e9_MH0001.trimmed.fa.abundfilt.unique |cut -f 1|sort -u >e9_MH0001.trimmed.fa.abundfilt.unique.sequence_id

e9_MH0001.trimmed.fa.abundfilt.abundfilt.unique.sequence_id: MH0001-reads.mer e9_MH0001.trimmed.fa.abundfilt.abundfilt
	gt tallymer search -output qseqnum qpos counts -tyr MH0001-reads  -q e9_MH0001.trimmed.fa.abundfilt.abundfilt >e9_MH0001.trimmed.fa.abundfilt.abundfilt.unique
	more e9_MH0001.trimmed.fa.abundfilt.abundfilt.unique |cut -f 1|sort -u >e9_MH0001.trimmed.fa.abundfilt.abundfilt.unique.sequence_id

e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.unique.sequence_id: MH0001-reads.mer e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt
	gt tallymer search -output qseqnum qpos counts -tyr MH0001-reads  -q e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt >e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.unique
	more e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.unique |cut -f 1|sort -u >e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.unique.sequence_id

e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt.unique.sequence_id: MH0001-reads.mer e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt
	gt tallymer search -output qseqnum qpos counts -tyr MH0001-reads  -q e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt >e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt.unique
	more e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt.unique |cut -f 1|sort -u >e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt.unique.sequence_id

	# get the number of remaining reads and number of bad reads
bad_reads.wc: e10_MH0001.trimmed.fa.abundfilt.unique.sequence_id \
	e10_MH0001.trimmed.fa.abundfilt.abundfilt.unique.sequence_id \
	e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.unique.sequence_id \
	e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt.unique.sequence_id \
	e9_MH0001.trimmed.fa.abundfilt.unique.sequence_id \
	e9_MH0001.trimmed.fa.abundfilt.abundfilt.unique.sequence_id \
	e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.unique.sequence_id \
	e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt.unique.sequence_id 

	wc *.sequence_id >bad_reads.wc 
remaining_reads.wc: e10_MH0001.trimmed.fa.abundfilt \
	e10_MH0001.trimmed.fa.abundfilt.abundfilt \
	e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt \
	e10_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt.abundfilt \
	e9_MH0001.trimmed.fa.abundfilt \
	e9_MH0001.trimmed.fa.abundfilt.abundfilt \
	e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt \
	e9_MH0001.trimmed.fa.abundfilt.abundfilt.abundfilt

	wc MH0001.trimmed.fa *.abundfilt >remaining_reads.wc
