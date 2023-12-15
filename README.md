# NOTE: tool has been added to the [Galaxy Project](https://galaxyproject.org/)'s [Tools-IUC repo](https://github.com/galaxyproject/tools-iuc/); future updates will be applied there, and it should be considered the official source of the tool:
- https://github.com/galaxyproject/tools-iuc/tree/main/tools/windowmasker

Legacy README follows
------------

WindowMasker
------------

This is a Galaxy Wrapper for WindowMasker. WindowMasker is a program that can mask out highly repetitive and low complexity DNA sequences within a genome using the sequence of the genome itself. 

The WinMask module works in two stages. During Stage 1, unit counts are collected and stored in a separate file. During Stage 2 that file is used to mask the input sequences. Usually the unit counts file is created once per genome and then used multiple times for masking. 

WindowMasker_mkcounts
======================
Stage 1: Generate a counts file

    $ windowmasker -mk_counts [-in input_file_name] [-out output_file_name] [-checkdup check_duplicates] [-t_low T_low] [-t_high T_high] [-fa_list input_is_a_list] [-mem available_memory] [-unit unit_length] [-genome_size genome_size] [-exclude_ids exclide_id_list] [-ids id_list] [-infmt input_format] [-sformat unit_counts_format] [-smem available_memory] [-use_ba use_bit_arrays]

   
WindowMasker_ustat
===================
Stage 2: WindowMasker reads the data generated in Stage 1 and a set of input DNA sequences to output information about masked subintervals. If "-dust true" is specified, then the corresponding algorithm of the DUST module is applied to the input sequences in addition to window based masking. When DUST module is run, the results of the DUST and WinMask modules are merged together in the output. Specifically, a base is masked if it is masked by either DUST or by WinMask.

    windowmasker -ustat unit_counts [-in input_file_name] [-out output_file_name] [-window window_size] [-t_thres T_threshold] [-t_extend T_extend] [-t_low T_low] [-t_high T_high] [-set_t_low score] [-set_t_high score] [-infmt input_format] [-outfmt output_format] [-dust use_dust] [-exclude_ids exclude_id_list] [-ids id_list] [-text_match text_match_ids] [-use_ba use_bit_arrays]

Output formats:
* Use the binary or text maskinfo ASN.1 output formats to generate the mask file for the NCBI BLAST+ makeblastdb tool
* Use the BED output format to generate a list of masked regions

Reference
==========
[NCBI C++ Toolkit Cross Reference -- WindowMasker](https://www.ncbi.nlm.nih.gov/IEB/ToolBox/CPP_DOC/lxr/source/src/app/winmasker/README)

Citation
=========

[1] Morgulis A, Gertz EM, Schaffer AA, Agarwala R. WindowMasker:
    Window based masker for sequence genomes. Submitted for publication.
