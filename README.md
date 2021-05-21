# gbru_planning

### short term

- Salmonella graph
  - [x] determine node coverage of xmfa vs pggb_5 vs pggb_250
    - [x] make table of "node,length,reads,num_reads_covering"
  - [x] Test different SPAdes parameters with simulated reads: k 21,33,55
    - [x] Coverage distribution of assembled contigs
    - [x] Get alignments, view in tubemaps - specifically nodes that don't align
  - [o] Compare graph with BWA
    - [ ] Take simulated reads of the 4 non-ref genomes -> assemble -> align to the source genome (CP004027.1) - uncovered areas comparable to source genome simulations?
    - [ ] How much of CP004027.1 is not covered when you align the same assembled simulated reads to it with BWA? Compare to GraphAligner
      - [ ] Some reads are legitimately unmapped in both. Might just be missing in simulated set. Need to simulate more reads.

- Genesieve
  - [x] Obtain the Arabidopsis QTL data
    1) Get all associations by paging thru 25/100/1000 at a time, increasing offset to get next page
    2) Get the phenotype desc with JSON parser
    3) Get the SNP Chr/location with JSON parser
    4) Write it down
    5) For each study...
        - Collect all SNPs
        - If many on one chromosome, do k-means of like 2 or 3
        - get k-means boundaries by sorting clusters, get centroid +-50kbp
        - use those as coordinates, obtain genes from gff 
  - [x] Complete functionality testing on rice test set
    - [x] Fix genesieve env on genesieve server: numpy/gensim incompatibility issue
    - [x] Run full pipeline tests with hardcoded data
  - [ ] Test and validate SQL queries
    - [ ] incorporate into genesieve.py when finished
  - [ ] Create a validation test
    - Using our test set, pull regions (~300kbp either side?) around "true" genes. Generate distribution of scores. Where is the 'true' gene? Now generate a random region with a random trait. What's that distribution? How do they differ? "true" value minus the median of the "false" values
    - Homology: what if there are tandem dupes? How many validated genes have tandem dupes/copies conflating results? see how many - if it's like 50% then mask them in test set
        - Check to see how often a validated candidate gene has duplicated genes next to/near it in the ~500kbp either side region.
