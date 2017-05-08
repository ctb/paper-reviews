A review of
[Squeakr: An Exact and Approximate k-mer Counting System](biorxiv.org/content/early/2017/03/29/122077).

------

This paper introduces the squeakr system for exact and inexact k-mer counting.

The paper is well written and I have been able to obtain and execute
the software, although I have not spent any time trying to reproduce
the benchmarks.

The long and glorious history of approximate and exact k-mer counting
in bioinformatics (for many different purposes) is particularly well
discussed, from my (admittedly biased) perspective.  I particularly
appreciate the discussion of De Bruijn graph traversal which is usually
omitted in k-mer counting papers.

squeakr implements both exact and inexact k-mer counting.  squeakr
appears to perform better (?) than all other k-mer counting systems in
both inexact and exact modes, although I am unable to decipher figure
2's shading (see below). squeakr also excels in point queries graph
traversal mode and batch queries applied to large collections of
already loaded k-mers.  As such, it is perhaps the most major advance
in k-mer counting I've seen in the last few years.  I should say that
we are already planning to integrate the underlying CQF into our own
khmer software for these reasons, and we have found it to be relatively
straightforward; our preliminary performance benchmarks match the ones
in this paper, which is reassuring.

squeakr also has the very nice property that it uses an approximate
membership query system from which k-mers can be removed, which is
important.

# Paper details:

I cannot distinguish KMC2 from squeakr inexact in the figures.

I could not figure out how the exact k-mer counting worked; the
wording in the section just above results (section 3) could be
improved here, in my view.

# Technical issues that should be addressed:

What commands were used to execute the benchmarks and measure the
results? Please specify in gory detail.

What version of the code was used? Please cut a release and give it a DOI
(perhaps via Zenodo).

Please describe (briefly in the paper, or perhaps in more detail on the
github repo) what kind of testing approach you used.  How do we know
that the k-mer counts are correct, basically, and how can we check for
ourselves in newer versions?

I have been able to run this on my own data (hurray!) but I am unclear
as to how to work with squeakr's k-mer counts. Right now it looks like
basically I need to hook in at the c++ level - true?  If so it should be
made clear that this is a nice (and very fast) proof of concept that
is not yet directly usable at the command line for k-mer counting.
(This is a documentation issue.)

# Technical upgrades:

Here are some optional issues you should think about, now or later --

1. On AWS, these are the magic commands needed to get squeakr compiled on
the following image:

ubuntu/images/hvm/ubuntu-wily-15.10-amd64-server-20160222 (ami-05384865)


```
sudo apt-get update
sudo apt-get install -y libboost-dev libssl-dev zlib1g-dev libbz2-dev make libboost-system-dev libboost-thread-dev
```

2. 'fallocate' doesn't exist on Mac OS X, so I was unable to make try
squeakr on Mac OS X.  This will inhibit a lot of bioinformaticians
from making use of squeakr.

# Miscellaneous questions

We have been thinking about using a rolling hash function in khmer;
see https://github.com/dib-lab/khmer/issues/1616. This seems like it
could make squeakr much faster if it replaced murmurhash. Thoughts?

Signed,

C. Titus Brown
titus@idyll.org
