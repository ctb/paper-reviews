The BIGSI paper introduces and demonstrates a massively scalable
approach to searching all available bacterial genomes from the ENA.
This is the first time this functionality is available, and this paper
outlines the utility of this by doing three types of searches across
all available data: a search for specific genes, defining the host
range of specific plasmids, and searching for antibiotic resistance
genes.

The paper is very well written and demonstrates the power of this
approach quite well.  While I would suggest adding one or two
sentences emphasizing the limitations of the chosen approach, BIGSI
shows a significant breakthrough in search capabilities and represents
a major advance in bioinformatics functionality.  The discussion does
a nice job of describing the opportunities of this new approach.

This paper follows on some other recent work - most notably the
Sequence Bloom Tree - but (as the authors state politely) is not
particularly comparable to these others due to differences in
emphasis, e.g. the application of SBTs is mostly intended for data
sets with an upper bound on k-mer abundance.  Limitations of
approaches like Mantis are well discussed and appropriately dismissed
as not particularly comparable yet. They do not mention MinHash/mash,
which is appropriate given the difference in emphasis (mash could not
do at least two of the three searches they implement in this paper).

The figures and discussion are detailed; the experiments are well designed
and comparisons are fair; and overall this is an impressively well done
paper!

The software is freely available and this group has a good history of
solid software development. I did not evaluate the software at all
myself.

As a methods developer myself, I could wish for more discussion of the
limitations of the approach.  Specifically, I think these issues shuold
be mentioned somewhere up front:

* BIGSI relies on (relatively) small queries

* searching for allelic variants requires combinatorial querying;

* the basic BIGSI approach relies on having small genomes / an upper
  fixed limit on size of database entries, and thus this is only
  suitable for bacterial genomes.  There is some discussion of how
  this could be resolved, but at least for now, this would not be
  particularly usable for searching big animal/plant genomes or
  metagenomes.

* the search is in nucleotide space, not protein space.

None of these are problematic in the context of the search problem
described in the paper, and all of these are mentioned in the text
somewhere, but I believe the paper would benefit from a short
discussion of these limitations so that methods-focused readers could
quickly understand whether this approach is reusable for their
question.
