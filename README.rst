Optimal haplotype assembly of polyploids
========================================

Summary
--------

Haplotype assembly of polyploids is an open issue in plant genomics.
Recent experimental studies have shown that available methods are not delivering satisfying results in practice.
We investigated integer linear programming (ILP) models to assemble optimal haplotypes in polyploids [1].
Our tool is available for non-commercial purposes subject to a license agreement.


Download
--------

The latest binaries for Linux can be downloaded from the `GitHub releases page <https://github.com/ComputationalGenomics/HaplotypeAssembler/releases/latest>`_.

Usage
-----

Our tool takes in input one `BAM/SAM <http://samtools.github.io/hts-specs/SAMv1.pdf>`_ file and one single-sample `VCF <http://samtools.github.io/hts-specs/VCFv4.2.pdf>`_ file.
It produces in output one single-sample VCF file that encodes phased variants.
All files must be **sorted by genomic coordinates**.

For instance, to assemble tetraploid haplotypes in a genomic region, execute the following command line:

::

  $ hassle --ploidy 4 --input-bam INPUT.bam --input-vcf INPUT.vcf --output-vcf OUTPUT.vcf

Option ``--dosages`` determines how strictly allelic dosages are regarded in the assembly:

* ``exact`` corresponds to the fully constrained model in [1].
* ``hard`` corresponds to model cMFR in [1].
* ``soft`` corresponds to model aMFR in [1].

To get a full list of options, invoke the command line tool with -h or --help.


Contact
-------

For questions or comments, feel free to contact:

* Enrico Siragusa <esiragu@us.ibm.com>
* Laxmi Parida <parida@us.ibm.com>


References
----------

1. Siragusa, E., Finkers, R., and Parida, L. (2018). Optimal haplotype assembly of polyploids.
