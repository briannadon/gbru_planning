# gbru_planning

### short term

- Salmonella graph
  - [ ] determine node coverage of xmfa vs pggb_5 vs pggb_250
    - [ ] make table of "node,length,reads,num_reads_covering"

- Genesieve
  - [ ] Complete functionality testing on rice test set
    - [ ] Fix genesieve env on genesieve server: numpy/gensim incompatibility issue
    - [ ] Run full pipeline tests with hardcoded data
  - [ ] Test and validate SQL queries
    - [ ] incorporate into genesieve.py when finished
  - [ ] Create a validation test
    - Using our test set, pull regions (~300kbp either side?) around "true" genes. Generate distribution of scores. Where is the 'true' gene? Now generate a random region with a random trait. What's that distribution? How do they differ? "true" value minus the median of the "false" values
    - Homology: what if there are tandem dupes? How many validated genes have tandem dupes/copies conflating results? see how many - if it's like 50% then mask them in test set
        - Check to see how often a validated candidate gene has duplicated genes next to/near it in the ~500kbp either side region.
