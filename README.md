# #EMBOIntegModelling23
[slides](https://docs.google.com/presentation/d/1TZtmbZ_JNX3tnYArUOn4cqHctJqcWaZyBo--Aa5mYy4)

- (1) [ColabFold](https://github.com/sokrypton/ColabFold)
- (2) Advanced AlphaFold [Notebook](https://colab.research.google.com/github/sokrypton/EMBOIntegModelling23/blob/main/alphafold_advanced.ipynb)
- (3) Do default run
- (4) **Using templates for monomer**
  1. Use default sequence
  2. Set msa_method="single_sequence", do full run. what happens?
  3. Set msa_method="single_sequence", template_mode="mmseqs2", do full run. what happens?
- (5) **Modifying MSA**
  1. Use PyMol (or any 3D viewer) to compare [1X0O](https://www.rcsb.org/structure/1X0O) to [2K7S](https://www.rcsb.org/structure/2K7S), how are these different?
  2. Set msa_method="mmseqs2", template_mode="none"
  3. Try model each of the sequence below, what conformation do you get? Do they match 1X0O or 2K7S?

  1X0O
  ```
  GAMDNVCQPTEFISRHNIEGIFTFVDHRCVATVGYQPQELLGKNIVEFCHPEDQQLLRDSFQQVVKLKGQVLSVMFRFRSKNQEWLWMRTSSFTFQNPYSDEIEYIICTNTNVKNSSQE
  ```

  2K7S
  ```
  GAMDNVCQPTEFISRHNIEGIFTFVDHRCVATVGYQPQELLGKNIVEFCHPEDQQLLRDSFQQVVKLKGQVLSVMFRFRSKNQEWLWMRTSSQTAQNPYSDEIETIICTNTNVKNSSQE
  ```
  4. create a code cell between prep_inputs and pre_analysis, try modify `msa` array. (hint: "X"=20, "-"=21, `msa[1:,?] = ?`)
  5. rerun the prediction
- (6) **Provide templates for multimer**
  1. Use sequence pair from [2NQD](https://www.rcsb.org/structure/2NQD)
     - Hint: Use ":" between sequences to indicate multimer input.
  2. Set msa_method="single_sequence", template_mode="mmseqs2", do full run.
     Run post_analysis="animate", what happens each recycle? How many recycles were needed to find solution?
  3. Set msa_method="mmseqs2", template_mode="mmseqs2", pair_mode="paired", do full run.
     Run post_analysis="animate", what happens each recycle? How many recycles were needed to find solution?
  4. Set msa_method="single_sequence", template_mode="custom", pdb="2NQD", chain="A,B", do full run.
     Run post_analysis="animate", what happens each recycle? How many recycles were needed to find solution?

## ANSWERS

-(5)
  ```python
  msa[1:,-27:] = 20
  deletion_matrix[1:,-27:] = 0
  ```
  - 20 = "X" unknown amino acid
  - deletion_matrix keeps track where there are insertions relative to first sequence.
  - `1:` beyond the first sequence ( we want to keep the first sequence untouched)
  - `-27:` last 27 positions
