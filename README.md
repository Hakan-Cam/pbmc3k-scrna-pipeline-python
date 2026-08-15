# PBMC3k scRNA-seq Pipeline — Python/Scanpy

Python/Scanpy implementation of the classic pbmc3k single-cell RNA-seq analysis pipeline,
built as a companion to a parallel R/Seurat implementation
(see: PBMC3k_scrnaseq_pipeline_R).

## Pipeline
1. Environment setup (pbmc3k_scrna conda env)
2. Data loading — pbmc3k triplet loaded into AnnData (2,700 x 32,738)
3. QC + Scrublet doublet removal -> 2,595 clean cells
4. Normalization, 2,000 HVGs, scaling
5. PCA -> UMAP -> Leiden clustering — 9 clusters
6. Marker detection (rank_genes_groups) -> 9 annotated cell types

## Notes
- Doublet detection: Scrublet (Python) vs scDblFinder (R) — different algorithms,
  slightly different clean cell counts (2,595 vs 2,526).
- Clustering: Leiden (Python) vs Louvain (R) — both recovered 9 clusters with
  consistent cell type identities.

See the R/Seurat companion repo for a side-by-side comparison of the two toolchains.
