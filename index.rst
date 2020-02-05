The ChIA-DropBox2 *(cdb2)* suite
================================

::

    cdb2 [sub-command] [options]

Sub-commands and Options of *cdb2*
----------------------------------

::

    CHIADROP
        -i FILE        input file name FILE: FILE is a bam file from longranger wgs pipeline named "phased*.bam";
        -schr FILE     select chromosomes you want, and list in FILE, format: per chromosome name per line.
        -q INT         skip aligments with MAPQ smaller than INT, default= 30.
        -cut INT       skip aligments with mappable sequence length smaller than INT bp, default= 50.
        -maxfn INT     skip clusters' total fragment count > INT, default INT = 5000.
        -minfn INT     skip clusters' total fragment count < INT, default INT = 2.
        -ext INT       extend INT bp for each read's 3' end, default= 500.
        -f2f INT       merge the two fragments, when their between-distance <= INT bp, default INT = 3000. 

::

    SPRITE
        -i FILE        input file name FILE: FILE is a SPRITE cluster file named ".clusters.gz"
        -schr FILE     select chromosomes you want, and list in FILE, format: per chromosome-name per line.
        -maxfn INT     skip clusters' total fragment count > INT, default INT = 5000.
        -minfn INT     skip clusters' total fragment count < INT, default INT = 2.
        -ext INT       extend INT bp for each read/fragment start position, default INT = 500.
        -f2f INT       merge the two fragments, when their between-distance <= INT bp, default INT = 3000. 

::

    GAM
        -i FILE        input file name FILE: FILE is a GAM matrix file named ".multibam.txt"
        -schr FILE     select chromosomes you want, and list in FILE, format: per chromosome name per line.
        -maxfn INT     skip clusters' total fragment count > INT, default INT = 5000.
        -minfn INT     skip clusters' total fragment count < INT, default INT = 2.
        -ext INT       extend INT bp for each read/fragment start position, default= 500.
        -f2f INT       merge the two fragments, when their between-distance <= INT bp, default INT = 3000. 

Examples of *cdb2*
------------------

::

    cdb2 CHIADROP -i test.chiadrop.bam -schr dm3.txt
    cdb2 SPRITE -i test.sprite.bam -schr hg38.txt -f2f 8000 -maxfn 3000
    cdb2 GAM -i test.gam.bam -schr mm9.txt -f2f 8000

Output of *cdb2*
----------------

1 ***.pc.bgz*** and ***.pc.bgz.tbi***

::

        for linear fragment cluster view in Chia-View2

2 ***.hic***

::

        for 2D heatmap view in Juicebox

3 ***.paircluster.bedpe.gz***

::

        for pairend loop-cluster view in IGV

4 ***.bedgraph***

::

        .rcov.bedgraph --- Coverage file generated from quilified reads
        .fcov.bedgraph --- Coverage file generated from fragments
        .acov.bedgraph --- Coverage file generated from PET anchors (without remove duplicated anchors).

5 ***.region.rds*** and ***.PEanno.rds***

::

        for linear fragment cluster view in Chia-View (version 1)    

Statistic information
---------------------

1 ***.sta.txt***

2 ***.log***

QA plots
--------

1 ***.qaplot.png***
