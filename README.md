# Bird Classifier

A small PyTorch project for classifying bird images using a pre‑trained ResNet backbone and a custom training pipeline built in Jupyter notebooks.

The main workflow lives in `notebook.ipynb`, which walks through the project in numbered parts:

- **Part 0–4**: Explore the dataset, build a custom `BirdDataset`, split into train/test, and create dataloaders.
- **Part 5–8**: Load a pre‑trained ResNet‑18 model, freeze the backbone, attach a custom classification head, and sanity‑check the model.
- **Part 9–20**: Define optimizer and loss, write training and inference loops, handle saving/loading checkpoints, and experiment with learning‑rate schedules (including cosine and one‑cycle policies).

---

## Project structure

- `notebook.ipynb` – main end‑to‑end notebook (data exploration, model, training, evaluation).
- `notes/course.ipynb` – course/learning notes (not required to run the model).
- `birds_data/` – local bird image dataset (ignored by git).
- `model_checkpoint/` – saved model checkpoints (ignored by git).
- `model/` – any exported models or artifacts you create locally.
- `.gitignore` – excludes data, checkpoints, and notebook checkpoints from version control.

You are expected to bring your own bird dataset in `birds_data/` with a structure similar to:

```text
birds_data/
  class_1/
    img_1.jpg
    img_2.jpg
    ...
  class_2/
    img_3.jpg
    ...
  ...
```

---

## Requirements

This project uses Python and PyTorch. A typical environment looks like:

- Python 3.9+ (3.10/3.11 also fine)
- `torch`
- `torchvision`
- `matplotlib`
- `Pillow`

You can start from something like:

```bash
pip install torch torchvision matplotlib pillow
```

If you are using Conda:

```bash
conda create -n bird-classifier python=3.10
conda activate bird-classifier
pip install torch torchvision matplotlib pillow
```

You can later export a full dependency list with:

```bash
pip freeze > requirements.txt
```

and commit that file to the repository.

---

## How to run

1. **Prepare data**
   - Place your bird image dataset under `birds_data/` using the folder structure shown above.

2. **Set up environment**
   - Create and activate a Python environment.
   - Install the requirements (see the section above).

3. **Run the notebook**
   - Start Jupyter:

     ```bash
     jupyter notebook
     ```

   - Open `notebook.ipynb`.
   - Run the cells in order from **Part 0** onward.

The notebook will:

- Scan the dataset and show basic statistics.
- Visualize random images from each bird class.
- Build and test the custom `BirdDataset` and dataloaders.
- Load a pre‑trained ResNet‑18 and adapt it to your number of classes.
- Train the classifier, evaluate it, and save/load checkpoints.
- Experiment with different learning‑rate schedules.

---

## Data and checkpoints

- **Dataset**: The full bird dataset is **not** committed to the repository. It is stored locally in `birds_data/` and ignored via `.gitignore`. In your own fork, either:
  - Place your private dataset there, or
  - Use a public bird dataset and document how to download it in your own README notes.

- **Model weights and checkpoints**: Saved to `model_checkpoint/` (and possibly `model/`) and also ignored by git. If you want to share trained weights, a better option is to upload them to an external storage (e.g. cloud storage or model hub) and link to them from the README.

---

## Notes

- This repository is designed primarily as a learning/experimenting project rather than a polished package.
- For production use, you might want to:
  - Move core logic (dataset, model definition, training loops) from the notebook into Python modules.
  - Add tests and continuous integration.
  - Add a small CLI or script (`train.py`, `infer.py`) that uses the same components outside of Jupyter.

