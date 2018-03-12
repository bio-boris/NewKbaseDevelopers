# The Genome Object
https://narrative.kbase.us/#spec/type/KBaseGenomes.Genome

Optional Fields

@optional cdss mrnas assembly_ref quality close_genomes analysis_events features source_id source contigs contig_ids publications md5 taxonomy gc_content complete dna_size num_contigs contig_lengths contigset_ref
@optional taxon_ref assembly_ref gff_handle_ref genbank_handle_ref external_source_origination_date release original_source_file_name notes environmental_comments reference_annotation quality_score methodology type

@metadata ws gc_content as GC content
@metadata ws taxonomy as Taxonomy
@metadata ws md5 as MD5
@metadata ws dna_size as Size
@metadata ws genetic_code as Genetic code
@metadata ws domain as Domain
    @metadata ws source_id as Source ID
    @metadata ws source as Source
    @metadata ws scientific_name as Name
    @metadata ws length(close_genomes) as Close genomes
    @metadata ws length(features) as Number features
    @metadata ws num_contigs as Number contigs
