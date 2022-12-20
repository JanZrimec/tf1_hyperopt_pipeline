# param_pipeline
Optimization of hyperparamers for deep learning models using hyperopt, snakemake, tensorflow 1, see environment export file for full dependency list.

Key files to edit:

data/ .. folder contains .npz file with training and test data splits, 4 lists of X_train, X_test, Y_train, Y_test, plus optionally gene names train and test. See provided examples.

models/ .. folder contains .py file with data loading, parameters and model architecture functions, called by the scripts. See provided examples.

params.yml .. contains general parameter ranges and definitions, as defined by optimization algorithms and packages used. For details check literature or with authors, in principle can be left as is.

config.yml .. master configuration file defining data and model file combinations and master parameters such as random seeds.

To run:

single job on 1 gpu:

`nohup snakemake -j 1 >> _run_hyperas_e500_i1500.log &`

4 parallel jobs on 2 gpu cluster:

`nohup snakemake -j 4 --resources gpu=200 mem_frac=160 --rerun-incomplete >> _run_hyperas_e500_i1500.log  2>&1 &`
