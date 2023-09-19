# #EMBOIntegModelling23
[slides](https://docs.google.com/presentation/d/1TZtmbZ_JNX3tnYArUOn4cqHctJqcWaZyBo--Aa5mYy4)

- (1) [ColabFold](https://github.com/sokrypton/ColabFold)
- (2) Advanced AlphaFold [Notebook](https://colab.research.google.com/github/sokrypton/EMBOIntegModelling23/blob/main/alphafold_advanced.ipynb)
- (3) Providing Templates
  1. Try set msa_method="single_sequence" what happens?
  2. Try set template_mode="mmseqs2" 
- (4) Modifying MSA
  1. Use PyMol (or any 3D viewer) to compare [1X0O](https://www.rcsb.org/structure/1X0O) to [2K7S](https://www.rcsb.org/structure/2K7S), how are these different?
  2. If you model each sequences, what conformation do you get?
  >1X0O
  ```
  GAMDNVCQPTEFISRHNIEGIFTFVDHRCVATVGYQPQELLGKNIVEFCHPEDQQLLRDSFQQVVKLKGQVLSVMFRFRSKNQEWLWMRTSSFTFQNPYSDEIEYIICTNTNVKNSSQE
  ```
  >2K7S
  ```
  GAMDNVCQPTEFISRHNIEGIFTFVDHRCVATVGYQPQELLGKNIVEFCHPEDQQLLRDSFQQVVKLKGQVLSVMFRFRSKNQEWLWMRTSSQTAQNPYSDEIETIICTNTNVKNSSQE
  ```
  3. create a code cell between prep_inputs and pre_optional_analysis, try modify `msa` array. (hint: 20 = "X", 21 = "-")
  4. rerun the prediction
