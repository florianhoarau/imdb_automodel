# imdb_automodel
Python (Polar) script to explore and modelize the imdb public dataset

The script will explore each table :

EXAMPLE :

Table "name.basics.tsv.gz" has Rows_MLN = 13.9 and columns = 6 :

Column "nconst" Type = "String" # Unique_MLN = 13.9 # Unique_pcts = 100.0% # Empty_pcts = 0.0% #  Prefix detected = nm #
Column "primaryName" Type = "String" # Unique_MLN = 10.7 # Unique_pcts = 77.0% # Empty_pcts = 0.0% #
Column "birthYear" Type = "Int64" # Unique_MLN = 0.0 # Unique_pcts = 0.0% # Empty_pcts = 95.0% #
Column "deathYear" Type = "Int64" # Unique_MLN = 0.0 # Unique_pcts = 0.0% # Empty_pcts = 98.0% #
Column "primaryProfession" Type = "String" # /!\ List detected with ratio 138.0% /!\ Unique_MLN = 0.0 # Unique_pcts = 0.0% # Empty_pcts = 19.0% #
Column "knownForTitles" Type = "String" # /!\ List detected with ratio 185.0% /!\ Unique_MLN = 5.8 # Unique_pcts = 42.0% # Empty_pcts = 11.0% #  Prefix detected = tt

Prefix detected : ['nm', 'tt']
Primary Key is ['nconst'] has size_MLN [13.9]
Foreign Key could be ['knownForTitles_exploded'] has size_MLN [5.8]
<bound method DataFrame.transpose of shape: (6, 6)
┌────────────┬────────────────────┬───────────┬───────────┬───────────────────┬────────────────────┐
│ nconst     ┆ primaryName        ┆ birthYear ┆ deathYear ┆ primaryProfession ┆ knownForTitles     │
│ ---        ┆ ---                ┆ ---       ┆ ---       ┆ ---               ┆ ---                │
│ str        ┆ str                ┆ i64       ┆ i64       ┆ str               ┆ str                │
╞════════════╪════════════════════╪═══════════╪═══════════╪═══════════════════╪════════════════════╡
│ nm9570225  ┆ Senarath           ┆ null      ┆ null      ┆ actor             ┆ tt7925724,tt790298 │
│            ┆ Mapitigama         ┆           ┆           ┆                   ┆ 2                  │
│ nm14116768 ┆ Danny Swart        ┆ null      ┆ null      ┆ null              ┆ tt0412116          │
│ nm9545314  ┆ Rachid Ouchen      ┆ null      ┆ null      ┆ composer          ┆ tt7855880          │
│ nm15880378 ┆ John Steward       ┆ null      ┆ null      ┆ null              ┆ null               │
│ nm14827535 ┆ Angel Mathyolweni  ┆ null      ┆ null      ┆ miscellaneous     ┆ tt27415828         │
│ nm11912394 ┆ Ryan Krank         ┆ null      ┆ null      ┆ null              ┆ tt8129504          │
└────────────┴────────────────────┴───────────┴───────────┴───────────────────┴────────────────────┘>

Then compute the detailed list of relationships :

EXAMPLE :

Matching of Primary Key title.basics.tsv.gz_tconst_tt_11.2
 PKey tconst from title.basics.tsv.gz has same prefix "tt" than FKey knownForTitles-exploded from name.basics.tsv.gz
 PKey tconst from title.basics.tsv.gz has same prefix "tt" than FKey titleId from title.akas.tsv.gz
 PKey tconst from title.basics.tsv.gz has same size than FKey titleId from title.akas.tsv.gz
 PKey tconst from title.basics.tsv.gz has same prefix "tt" than FKey parentTconst from title.episode.tsv.gz
 PKey tconst from title.basics.tsv.gz has same prefix "tt" than FKey tconst from title.principals.tsv.gz
 PKey tconst from title.basics.tsv.gz has close size with FKey tconst from title.principals.tsv.gz Deltasize_MLN =1.0
 PKey tconst from title.basics.tsv.gz has same prefix "tt" than FKey tconst from title.principals.tsv.gz
 PKey tconst from title.basics.tsv.gz has close size with FKey tconst from title.principals.tsv.gz Deltasize_MLN =1.0

and finally show the relationships summary :

![image](https://github.com/user-attachments/assets/859d3faf-b401-4c5c-a4bf-6afb3f0562d1)

