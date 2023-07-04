# DLKcat on PLEX

DLKcat, a deep learning approach for Kcat prediction, is a tool that predicts enzyme catalytic activity based on protein sequences and compound SMILES. This README guides you on how to run DLKcat using PLEX, a simple client for distributed computation.

## Docker

DLKcat on PLEX runs in a Docker container to ensure software consistency. The Dockerfile pulls a conda-based Python image and installs necessary libraries including PyTorch, scikit-learn, Biopython, pandas, scipy, numpy, seaborn, matplotlib, and RDKit. It then clones the DLKcat package from GitHub, navigates to the `DeeplearningApproach` directory, and unzips `input.zip`.

## Input

To run DLKcat, prepare an `input.tsv` file that contains your protein sequences and compound SMILES. The file should be structured as follows:

- The first column should contain the protein sequence.
- The second column should contain the substrate (compound) SMILES.
- You can also include the substrate name in the third column, but this is optional.

Please note that the Docker command by default expects this file at `/app/DLKcat/DeeplearningApproach/Code/example/input.tsv`.

## Running DLKcat

The `batch_dlkcat.json` file details how to run the DLKcat tool on PLEX. The Docker image referenced here should be built from the provided Dockerfile. 

To use this setup, follow these steps:

1. Install PLEX following the instructions on the main PLEX page.
2. Clone the PLEX repository and navigate to the `tools/dlkcat` directory.
3. Prepare your `input.tsv` file with protein sequences and substrate SMILES.
4. Use the `batch_dlkcat.json` file to submit your PLEX job as follows:
    ```bash
    ./plex create -t tools/dlkcat/batch_dlkcat.json -i /path/to/your/input.tsv --autoRun=True
    ```

The command above will run DLKcat and generate an `output.tsv` file in your specified output directory. This output file will contain the predicted Kcat values for your input protein sequences and compound SMILES.

---
