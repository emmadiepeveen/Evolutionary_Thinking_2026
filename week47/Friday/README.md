# Friday Week 47

## PCA of ancient and modern Eurasians

Today we **read** a PCA instead of running one. You get the output of a principal components
analysis of ~1,000 West Eurasian and ~300 East Eurasian individuals, part of it ancient DNA, and
work out what it says about European and Siberian population history.

The West Eurasian analysis recreates the PCA in
[Mathieson et al. (2015), *Nature* 528:499–503](https://doi.org/10.1038/nature16152),
*Genome-wide patterns of selection in 230 ancient Eurasians* (you don't have to read the paper).

> **Not Wednesday's paper.** Wednesday's discussion was Bergeron et al. (2023) on germline mutation
> rates, which has nothing to do with this exercise. An earlier version of this page said the two
> were connected — they aren't.

Along the way you will:

- see what `smartPCA` was actually given, and why ancient samples are **projected** onto modern
  variation instead of helping to compute the axes;
- read a PCA plot properly — including why **in this dataset you cannot judge a PC's importance
  from how wide the cloud looks**;
- connect the clusters to real processes: drift, founder effects, gene flow, isolation by distance,
  admixture;
- measure how well each PC separates your populations, instead of guessing;
- find the data errors in the files you were given. There are several, and plotting finds them.

## The tutorial

Same content in both languages — pick whichever you prefer.

| | With the exercises to fill in | Fully worked |
|---|---|---|
| **R** (ggplot2) | [`exercise/pca_eurasia.Rmd`](exercise/pca_eurasia.Rmd) | [`exercise/pca_eurasia_solved.Rmd`](exercise/pca_eurasia_solved.Rmd) |
| **Python** (pandas) | [`exercise/pca_eurasia.ipynb`](exercise/pca_eurasia.ipynb) | [`exercise/pca_eurasia_solved.ipynb`](exercise/pca_eurasia_solved.ipynb) |

The exercise versions contain 📝 **TODO** blocks where you write a few lines yourself, with
💡 **hints** for the syntax, check cells that tell you whether you got it right, and ✅ **Reveal**
buttons holding the code.

The ❓ **Question** blocks are there to make you think before you write. The **answers to the
hand-in questions are not in these files** — those are what you are being asked for. A couple of
warm-up questions that are *not* part of the hand-in do keep their answers behind a reveal button,
so you can check your understanding as you go.

**Prefer to focus on the concepts rather than the coding?** Use a *solved* version: the same
document with all the code already filled in, so you can just run it and work through the questions.

### How to run it

**R:** open `exercise/pca_eurasia.Rmd` in RStudio and run it **chunk by chunk** (the green ▶ button).
You only need `ggplot2`:

```r
install.packages("ggplot2")
```

Don't press *Knit* on the exercise version — it contains `TODO` placeholders, so it won't knit until
you have filled them in. The `_solved.Rmd` knits as it is.

**Python:** pick one of

1. **Google Colab (nothing to install):**
   [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/emmadiepeveen/Evolutionary_Thinking_2026/blob/main/week47/Friday/exercise/pca_eurasia.ipynb)
   Run the optional install cell at the top; the data download themselves.
2. **Your own Jupyter / VS Code:** open the notebook and run the optional install cell at the top.
3. **Conda/mamba:**
   ```bash
   mamba env create -f env.yaml
   mamba activate evolutionary-thinking-week47
   jupyter lab
   ```

Everything runs in well under a minute on any laptop.

## Data

The files are in [`data/`](data/) as plain tab-separated text (the `.zip` versions in this folder
are the originals, kept for reference). The tutorial loads them for you.

| File | Contents |
|---|---|
| `dataWE.txt` | 997 West Eurasian individuals: ID, PC1–PC10, population, group |
| `dataEE.txt` | 296 East Eurasian individuals, same columns — a **separate** PCA with its own axes |
| `dataWE_LatLong.txt` | Latitude/longitude of the excavation site, for 191 of the 220 ancient individuals |

### Things the old version of this page got wrong

These tripped people up every year, so they are worth stating plainly. All of them are explained in
the tutorial where they matter.

- **`ModAnc` is not "modern or ancient".** It has **six** values — `Modern`, `Hunter-gatherer`,
  `EHG`, `Early-farmer`, `Steppe`, `Samara_Eneolithic` — which are archaeological/ancestry groups.
  There is no value `"Ancient"`, so filtering for it silently gives you nothing.
- **Three population names are mangled**: `Modernaltese`, `Modernordovian` and `Modernotala_HG` are
  really `Maltese`, `Mordovian` and `Motala_HG`. Someone replaced `M` with `Modern` across the whole
  file.
- **Eight rows of `dataWE_LatLong.txt` have latitude and longitude swapped**, putting Bronze Age
  Europeans in the Gulf of Aden and the Arctic Ocean. Fixing them takes PC1 ~ latitude from
  r = −0.38 to r = −0.69.
- **There are no eigenvalues**, and `smartPCA` normalised every PC to unit length — so all ten axes
  have exactly the same spread. You cannot report variance explained, and you must not infer a PC's
  importance from the width of its cloud.
- **`Russia_Baikal` is not an Arctic group** despite being listed with three Yupik/Unangax̂
  populations; Lake Baikal is deep in continental Siberia, and the data show it behaving
  accordingly.

## Hand-in

The questions are **hand-in exercise 3**, to be submitted on Brightspace (see also
[`handin_3/`](../../handin_3)). Each question is marked **📝 Hand-in question N** in the tutorial, in
the section that gives you the tools for it, and there is a checklist at the end.

| Hand-in question | Where |
|---|---|
| 1. PC1 vs PC2 of `dataWE`, coloured by `ModAnc` | §4 |
| 2. English, Norwegian, Finnish, Icelandic | §6 |
| 3. Four populations of your choice | §6 |
| 4. PC3 vs PC4 of those four | §7 |
| 5. Combinations of PC5–PC10, and why | §7 |
| 6. Correlate latitude/longitude with PC1 and PC2 | §8 |
| 7. PC1 vs PC2 of `dataEE` | §9 |
| 8. PC3 vs PC4 of `dataEE` | §9 |
| 9. aDNA artefacts that make ancient samples unsuitable for computing PCs | §2 and §10 |
| 10. What other data can you analyse with PCA | §10 |

(Section numbers are the same in the R and Python versions.)
