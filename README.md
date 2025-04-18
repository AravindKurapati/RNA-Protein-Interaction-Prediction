# RNA-Protein Interaction Prediction with Multimodal Deep Learning

## **Overview**
This repository focuses on predicting **RNA–Protein interactions** using a **multimodal deep learning framework** that combines:

-  **BioBERT embeddings** for RNA sequences  
-  **ESM2 protein embeddings** for protein sequences  
-  **Tabular features** capturing structural and biochemical RNA properties  

The goal is to develop a biologically-grounded model that generalizes across RNA-binding proteins and provides interpretable results.

---



 **Model Architecture**:  
- Multimodal model (BioBERT + ESM2 + MLP)

 **Input Features**:
- `RNA_sequence` → BioBERT  
- `protein_sequence` → ESM2  
- `tabular_features` → MLP  

 **Labels**:  
- Binary classification: Interaction = `1`, No interaction = `0`

## **Dataset Structure**

Each row in the dataset includes:

- `rna_sequence`: Nucleotide sequence of the RNA  
- `protein_sequence`: Amino acid sequence of the protein  
- `tabular_features`: Engineered features (e.g. GC content, loop energy, etc.)  
- `label`: Binary interaction label (1 or 0)

Preprocessing includes:
- Cleaning FASTA-format sequences
- Generating embeddings from pretrained models
- Scaling tabular features

---

## ** Methodology**

### **1️ BioBERT Embeddings (RNA)**
- Using `dmis-lab/biobert-v1.1`
- CLS token from final hidden state used as RNA representation

### **2️ ESM2 Embeddings (Protein)**
- Using `facebook/esm2_t6_8M_UR50D`
- Mean-pooled representation over amino acid tokens

### **3️ Tabular Features**
- Processed through a simple feed-forward network
- Include numeric descriptors derived from RNA structure

### **4️ Multimodal Fusion**
- Concatenate all three components
- Apply a final classification head (sigmoid for binary classification)

---



## **🔗 Related Tools & Libraries**

- [HuggingFace Transformers](https://huggingface.co/)
- [Facebook ESM Models](https://github.com/facebookresearch/esm)

---


##  Citation

**BioBERT**  
Lee, J., Yoon, W., Kim, S., Kim, D., So, C.H., & Kang, J. (2020).  
*BioBERT: a pre-trained biomedical language representation model for biomedical text mining*.  
Bioinformatics, 36(4), 1234–1240.  
[Paper Link](https://academic.oup.com/bioinformatics/article/36/4/1234/5566506) • [Hugging Face Model](https://huggingface.co/dmis-lab/biobert-v1.1)

---

**ESM2**  
Lin, Z., Akin, H., Rao, R., Hie, B., et al. (2023).  
*Language models of protein sequences at the scale of evolution enable accurate structure and function prediction*.  
bioRxiv.  
[Paper Link](https://www.biorxiv.org/content/10.1101/2022.07.20.500902v2) • [GitHub](https://github.com/facebookresearch/esm) • [Hugging Face Model](https://huggingface.co/facebook/esm2_t6_8M_UR50D)

