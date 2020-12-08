# Build neo4j graph

## Part 1: KEGG backbone

1.1 Download KEGG compounds and reactions using KEGGREST:
    
    RScript get_KEGG.R

1.2 Parse KEGG download

Run the parse_data_KEGG.ipynb jupyter notebook. 
    
1.3 Import KEGG into neo4j

Run the parse_data_KEGG.ipynb jupyter notebook. 

## Part 2: Proteome data

Proteome data files needed are:

* CruxOutput/*percolator.target.proteins.txt
* CruxOutput/*.02.spectral-counts.target.txt
* UpdatedMetaData.txt
* AccessionsClusteredAt100ID.tab
* scaffold2bin.tsv
* DiamondPreterm.emapper.annotations
* uniprot-proteome_UP000005640_Cluster100.emapper.annotations

2.1 Download KEGG keys

    wget http://rest.kegg.jp/link/rn/ko -O "./data/KEGG/ko-to-rn-api.txt"
    wget http://rest.kegg.jp/link/ec/ko -O "./data/KEGG/ko-to-ec-api.txt"
    wget http://rest.kegg.jp/link/rn/ec -O "./data/KEGG/ec-to-ko-api.txt"

2.2 Prepare proteome data

Run the parse_data_proteome.ipynb jupyter notebook. 

2.3 Import proteome data into neo4j

Run the import_neo4j_proteome_data.ipynb jupyter notebook. 

