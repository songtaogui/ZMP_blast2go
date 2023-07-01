# ZMP_blast2go

A blast2GO like annotation pipeline for ZEAMAP.

## Installation

1. make sure these tools were installed and available through `$PATH`:

    - [diamond](https://github.com/bbuchfink/diamond)
    - [csvtk](https://github.com/shenwei356/csvtk)

2. Clone this repos, make the ZMP_blast2go script executable, and add to `$PATH`

    ```bash
    git clone https://github.com/songtaogui/ZMP_blast2go.git
    cd ZMP_blast2go/bin
    chmod +x ZMP_blast2go
    # you may add the dir to $PATH via:
    # echo "export PATH=$PWD:\$PATH" >> $HOME/.bashrc
    ```

## Usage

```
------------------------------------------------------------
Blast to GO pipelines for ZEAMAP DB
------------------------------------------------------------
Dependence:
[diamond](https://github.com/bbuchfink/diamond)
[csvtk](https://github.com/shenwei356/csvtk)
------------------------------------------------------------
USAGE:
    bash ZMP_blast2go [OPTIONS]

OPTIONS: ([R]:required  [O]:optional)
    -h, --help                          show help and exit.
    -t, --threads       <num>   [O]     set threads (default: 2)
    # I/O
    -i, --input         <file>  [R]     input protein file in fasta format.
    -d, --db            <file>  [O]     input path to NCBI NR database in dmnd format,
                                        default: parse the NR_DIAMOND_DB env.
    -m, --idmap         <file>  [O]     input nr_to_go idmap file (can be downloaded from link below).
                                        default: parse the SWISSPROT2GO_IDMAP env
    -o, --output        <str>   [O]     output name, will output results with this prefix,
                                        default: "zmp_nr2go_out".
    --blastpfile        <file>  [O]     prebuilt blastp file (with format listed blow),
                                        if provided, will skip on the fly diamond run.
    # OPT
    -e, --evalue        <0-1>   [O]     set evalue threshold (default: 1e-5)
    --quiet                             keep quiet, only output fatal errors
    --verbose                           be verbose, output detailed logs

NOTE:
    1. Swissprot idmap file download url:
    https://ftp.uniprot.org/pub/databases/uniprot/knowledgebase/idmapping/idmapping_selected.tab.gz
    2. If you provide a prebuilt blastp file, please make sure the file is in format of:
    NCBI blast --outfmt 6 sseqid slen sstart send qseqid qlen qstart qend
------------------------------------------------------------
Author: Songtao Gui
E-mail: songtaogui@sina.com
```

## Example

Go to the `test` dir and run `bash run_test.sh`

