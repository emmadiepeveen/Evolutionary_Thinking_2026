# Friday Week 44

## Population structure of goats and an introduction to PCA

Today we use **Principal Component Analysis (PCA)** to look at the genetic structure of 4,653 goats from 144 breeds sampled worldwide. We partly recreate the analysis from [Colli et al. (2018), *Genet Sel Evol* 50:58](https://doi.org/10.1186/s12711-018-0422-x) (you don't have to read the paper).

Along the way you will:
- learn how SNP genotype data are stored (PLINK `.bed/.bim/.fam` files),
- do the standard quality control filters yourself, and understand *why* each one is needed,
- run a PCA and learn how to read the plot,
- connect the patterns to evolution: genetic drift, gene flow, admixture and the history of goat domestication.

**The notebook: [`exercise/pca_goats.ipynb`](exercise/pca_goats.ipynb)**

It explains the concepts and the Python packages as you go. It contains 📝 **TODO** exercises where you write a few lines of code yourself (with 💡 hints for the syntax), check cells that tell you whether you got it right, and ✅ **Reveal** buttons with the solutions and the answers to the questions.

**Prefer to focus on the concepts instead of the coding?** Use [`exercise/pca_goats_solved.ipynb`](exercise/pca_goats_solved.ipynb) instead: the same notebook with all the code already filled in, so you can just run all the cells and work through the questions.

## How to run it

Pick **one** of these options:

1. **Google Colab (easiest, nothing to install):** [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/emmadiepeveen/Evolutionary_Thinking_2026/blob/main/week44/Friday/exercise/pca_goats.ipynb)
   Run the optional install cell at the top. The data are downloaded automatically.
2. **Your own Jupyter (JupyterLab, VS Code, ...):** open `exercise/pca_goats.ipynb` and run the optional install cell at the top. It installs any missing packages into the Python that runs the notebook, so you don't need to set up an environment.
3. **Conda/mamba (if you prefer a separate environment):**
   ```bash
   mamba env create -f env.yaml
   mamba activate evolutionary-thinking-week44
   jupyter lab
   ```

The data (`data/snps.bed`, `.bim`, `.fam`) are in this folder. If the notebook can't find them, it downloads them (~45 MB).

The whole notebook runs in about a minute (plus a few more for the optional exercises) and needs a few GB of memory (fine on Colab and most laptops).
