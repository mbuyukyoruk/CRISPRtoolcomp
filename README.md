# CRISPRtoolcomp

Author: Murat Buyukyoruk

        CRISPRtoolcomp help:

This script is developed to compare CRISPR hits coming from different detection software (i.e., CRISPRDetect, CRISPRClassify, CRISPRCASFinder, etc). 

Syntax:

    python CRISPRtoolcomp.py -i demo_CRISPR_list.txt

### Input file example:

Example Dataframe for the demo_CRISPR_list.txt file (tab separated excel file is required):

    Accession   Start   Stop    Tool
    NC_000853.1	412     3106	CRISPRDetect
    NC_000853.1	369170	369732	CRISPRDetect
    NC_000853.1	396568	397134	CRISPRDetect
    NC_000853.1	409295	410924	CRISPRDetect
    NC_000853.1	1519912	1520476	CRISPRDetect
    NC_000853.1	1631789	1632017	CRISPRDetect
    NC_000853.1	1779875	1780702	CRISPRDetect
    NC_000853.1	412     3105	CRISPRCASFinder
    NC_000853.1	369170	369731	CRISPRCASFinder
    NC_000853.1	396568	397133	CRISPRCASFinder
    NC_000853.1	409295	410923	CRISPRCASFinder
    NC_000853.1	1519912	1520474	CRISPRCASFinder
    NC_000853.1	1779810	1780701	CRISPRCASFinder

### Output files

A .clstr file will be generated to report the clusters of common CRISPRs detected from different software. Additionally, .log file will be generated to report unique occurences of each CRISPR arrays and first occurences in any given detection tool (lines with '*' in the .clstr file).

The format of .clstr file will look like:

    (Accession) (Start) (Stop)  (Tool)          ...     (Cluster_id)    (Similarity)        ...     (Coverage)
    NC_000853.1 412     3106    CRISPRDetect    ...	    1	            *
    NC_000853.1 412     3105    CRISPRCASFinder ...	    1	            0.9996288047512992	...	1.0
    NC_000853.1 369170  369732  CRISPRDetect    ...	    2	            *
    NC_000853.1 369170  369731  CRISPRCASFinder ...	    2	            0.998220640569395	...	1.0
    NC_000853.1 396568  397134  CRISPRDetect    ...	    3	            *
    NC_000853.1 396568  397133  CRISPRCASFinder ...	    3	            0.9982332155477032	...	1.0
    NC_000853.1 409295  410924  CRISPRDetect    ...	    4	            *
    NC_000853.1 409295  410923  CRISPRCASFinder ...	    4	            0.9993861264579497	...	1.0
    NC_000853.1 1519912 1520476 CRISPRDetect    ...	    5	            *
    NC_000853.1 1519912 1520474 CRISPRCASFinder ...	    5	            0.9964539007092199	...	1.0
    NC_000853.1 1631789 1632017 CRISPRDetect    ...	    6	            *
    NC_000853.1 1779810 1780701 CRISPRCASFinder ...	    7	            *
    NC_000853.1 1779875 1780702 CRISPRDetect    ...	    7	            0.9270482603815937	...	0.9987908101571947

Finally, a venn diagram will be generated if the input file contains data from a maximum of 4 unique CRISPR detection tools.

![Venn_diagram_example](https://github.com/mbuyukyoruk/CRISPRtoolcomp/blob/main/demo_CRISPR_hits_venn.png)

R is required to generate plots with various CRAN packages (i.e., ggvenn and its depencencies). 
The R script is generated to install CRAN packages if they were not available in the system, 

CRISPRtoolcomp dependencies:

R                                       refer to https://rstudio-education.github.io/hopr/starting.html

tqdm                                    refer to https://pypi.org/project/tqdm/

Input Paramaters (REQUIRED):
----------------------------
	-i/--input      Filename    Specify input file contain CRISPR array informations (with following headers separated with tab: Accession, Start, Stop, Tool).

Basic Options:
--------------
	-h/--help       HELP        Shows this help text and exits the run.
