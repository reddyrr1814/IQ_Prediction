
# IQ_Pred

This repository contains code and notebooks used for IQ prediction experiments using rs-fMRI data (ABIDE) and a hybrid Hydra-based multivariate regressor. The notebooks include preprocessing outputs, similarity/correlation matrices computed from temporal signals, CNN feature extraction experiments, and a hybrid model combining temporal and relational features.

Contents
- `abide_hydra.ipynb`: Uses ABIDE-provided numpy files (publicly available). Implements the Hydra multivariate regressor pipeline — run the notebook cell-by-cell in order to reproduce preprocessing, training, and evaluation outputs. This notebook also contains the hybrid variant that combines temporal and relational features for IQ prediction. See `new_CM_similarity.ipynb` for detailed feature construction used by the hybrid model.
- `hcp_hybrid.ipynb`: Evaluation notebook to verify the generalizability of the proposed Hybrid model on HCP-derived data or held-out subjects. Use this to test transfer and robustness of the hybrid approach.
- `new_CM_similarity.ipynb`: Computes multiple time-series similarity/distance measures from ABIDE rs-fMRI temporal information: correlation, coherence, PLI, PLV, DTW, and LCSS. These matrices are then fed to a CNN to extract feature combinations; the best-performing feature combinations are used as input to the hybrid model described in `abide_hydra.ipynb`.

Getting started
- Clone or open this workspace and launch Jupyter Notebook / JupyterLab in the project root.
- Open the notebooks in the following recommended order:
	1. `new_CM_similarity.ipynb` — compute similarity/coherence/distance matrices and extract CNN features.
 2. `abide_hydra.ipynb` — run the Hydra multivariate regressor and hybrid experiments using the precomputed features.
 3. `hcp_hybrid.ipynb` — run generalizability experiments using HCP or alternative data.

Data
- ABIDE rs-fMRI-derived numpy files are expected by `abide_hydra.ipynb` and `new_CM_similarity.ipynb`. These are publicly available from the ABIDE dataset portal; ensure you have the processed timeseries saved as numpy arrays in the paths used by the notebooks (update paths in the first cells as needed).

Dependencies
- Python 3.8+ recommended.
- Typical libraries used across the notebooks (install as needed):
	- `numpy`, `scipy`, `pandas`
	- `scikit-learn`
	- `tensorflow` or `keras` (if CNN models are implemented in Keras/TensorFlow)
	- `matplotlib`, `seaborn`
	- optional: `dtaidistance` (DTW), `numba`, or other specialized packages for similarity measures

Usage notes
- Run cells sequentially — many cells depend on outputs created earlier in the notebook.
- Large intermediate files (similarity matrices, CNN feature outputs) may be generated; confirm available disk space.
- Hyperparameters and dataset paths appear in the top cells of each notebook — edit those before running the experiments.

Results and reproducibility
- The notebooks include training and evaluation code; reproduce results by following the cell order and ensuring identical data inputs and random seeds (where specified).

Adding files to the repo
- To add a license, `.gitignore`, or CI, create the file in the repository root and commit; example `.gitignore` for Python projects typically includes `__pycache__/`, `.ipynb_checkpoints/`, and virtual environment folders.

Contact
- For questions about the code or data usage, open an issue in the repository or contact the maintainer.

License
- No license is included by default. Add a `LICENSE` file if you want to make the code publicly reusable (e.g., MIT License).

