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

## ** Citation**

@article{lee2020biobert,
  title={BioBERT: a pre-trained biomedical language representation model for biomedical text mining},
  author={Lee, Jinhyuk and Yoon, Wonjin and Kim, Sungdong and Kim, Donghyeon and So, Chan Ho and Kang, Jaewoo},
  journal={Bioinformatics},
  volume={36},
  number={4},
  pages={1234--1240},
  year={2020},
  publisher={Oxford University Press}
}
Model repo: https://huggingface.co/dmis-lab/biobert-v1.1


@article{lin2023esm2,
  title={Language models of protein sequences at the scale of evolution enable accurate structure and function prediction},
  author={Lin, Zeming and Akin, Haydar and Rao, Roshan and Hie, Brian and others},
  journal={bioRxiv},
  year={2023},
  publisher={Cold Spring Harbor Laboratory}
}
GitHub repo: https://github.com/facebookresearch/esm
Model repo: https://huggingface.co/facebook/esm2_t6_8M_UR50D
---
