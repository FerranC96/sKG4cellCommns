# yaleCollab_TAPE-KRISHNASWAMY

Yale Collab with Aarthi (Smita Krishnaswamy group). KGE of multiomics single-cell communications and signalling

##  KG design

### What we need
* Capture cell communications from L-R 
* Capture signalling changes via PTMs 
* Summarise above as pathways 
* Who sends, who receives? 
* Compare between cells, clusters, conditions 
    * Sc distance metric 

#### **Summary** 
L --> R --> PTMs 

Idea of talking (Ligands), hearing (receptors), and listening (PTMs) 

### Resources
* NicheNet
* CellChat
* REACTOME

### Methods
* Pathways should be edge annotations (essentially, annotating the triples with a single/list of pathways) 
    * Pathway annotations: From the 6 1st level REACTOME pathways (assuming most/all L, R, PTMS are present in those) 
        * 2nd level REACTOME pathway annotations (for visualisation?) 
        * 3rd level REACTOME pathway annotations for metadata? 
    * Per pathway: Measure GEx/intensity of entities 
        * Analyse the 3 distinct layers: Formally define dominance? 
            * Ligand dominance -> sender 
            * Receiver dominance -> receiver 
            * PTM dominance ->  ???? 
        * Summary pathway score: 
            * Define cell/group of cells 
            * Absolute value: Biased by pathway importance to cell 
            * Relative value: (aka EMD with all cells as reference) Relative importance of pathway on different cells 
            * ~~Should PTMs provide positive/negative scores? (i.e. inhibitors/activators)~~ 
* KGE: Explore pathway annotations 
* Diffusion method on KG: How the L, R and PTMs relate to one another 
    * Wavelets 
* Cells as signals on the graph: 
    * Project 
    * Compare across cells 

### Process
* Handle all 3 sources of data at once: DBs, scRNAseq and cytof 
    * Read databases: L and R list
    * Read cytof data: PTMs 
* Build KG: From entities above, define 2 types of relations: 
    * L-R cell commns 
    * Entity-entity (L to R and R to PTM) interaction if both in the same reactome pathway level 
* Process sc data: 
    * Filter data to KG entities and process both modalities 
    * All cells from both modalities should add up to same value 
* Downstream analyses 
    * Project sc data: 
        * Compute distances between cells
            * DR for single modality
            * DR for integrated modalities 
        * Cluster cells based on said distance: Functional communication groups 
    * Compute pathway scores: **Can we compute intensity of signal of cell on each node of the KG?** How different would that be from just GEx/AbIntensity 
        * Summary pathway score (per cell, per FC cluster) 
        * Layer analysis: sender/receiver (per cell, per FC cluster) 
    * Inference:
        * In silico pathway ablation -> rebalancing of KG
            * New distance prediction 
        * In silico ligand modulation -> simulate ligand presence at diff intensities 
            * New distance and pathway score predictions 
