Optimal haplotype assembly of polyploids
========================================

Summary
--------

Haplotype assembly of polyploids is an open issue in plant genomics.
Recent experimental studies have shown that available methods are not delivering satisfying results in practice.
We investigated integer linear programming (ILP) models to assemble optimal haplotypes in organisms with ploidy up to 4.
Our tool is available for non-commercial purposes subject to a license agreement.

Included are also example input files and programs to evaluate phasing results for MEC or haplotyping distance as described in the reference publication.

Reference
---------

Siragusa, E., Haiminen, N., Finkers, R., Visser, R. and Parida, L. (2018). Haplotype assembly of autotetraploid potato using integer linear programming.

Contact
-------

For questions or comments, feel free to contact: Laxmi Parida <parida@us.ibm.com>

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

  $ haplotype-assembler --ploidy 4 --input-bam INPUT.bam --input-vcf INPUT.vcf --output-vcf OUTPUT.vcf

Option ``--dosages`` determines how strictly allelic dosages are regarded in the assembly:

* ``exact`` corresponds to the fully constrained model in [1].
* ``hard`` corresponds to model cMFR in [1].
* ``soft`` corresponds to model aMFR in [1].


Detailed usage below by running  $ haplotype-assembler --help

====================================================================

SYNOPSIS  haplotype-assembler [OPTIONS] -ib <BAM FILE IN> -iv <VCF FILE IN>

DESCRIPTION

OPTIONS
    -h, --help
          Display the help message.
    --version-check BOOL
          Turn this option off to disable version update notifications of the
          application. One of 1, ON, TRUE, T, YES, 0, OFF, FALSE, F, and NO.
          Default: 1.
    --version
          Display version information.
    -v, --verbose
          Output verbose information to standard error.
    -ib, --input-bam INPUT_FILE
          Input SAM/BAM file. Valid filetypes are: .sam[.*] and .bam, where *
          is any of the following extensions: gz and bgzf for transparent
          (de)compression.
    -iv, --input-vcf INPUT_FILE
          Input VCF file. Valid filetype is: .vcf[.*], where * is any of the
          following extensions: gz and bgzf for transparent (de)compression.
    -ov, --output-vcf OUTPUT_FILE
          Output VCF file. Default: output to standard output. Valid filetype
          is: .vcf[.*], where * is any of the following extensions: gz and
          bgzf for transparent (de)compression.
    -oh, --output-het
          Output only heterozygous variants in the VCF file.
    -p, --ploidy INTEGER
          Organism ploidy. In range [1..4]. Default: 4.
    -d, --dosages STRING
          Use dosages from the input VCF file as hard or soft constraints, or
          ignore them. One of ignore, exact, hard, and soft. Default: exact.
    -c, --coverage INTEGER
          Minimum coverage per allele. In range [1..20]. Default: 1.
    -t, --timeout INTEGER
          Timeout in seconds. In range [0..3600]. Default: 0.
