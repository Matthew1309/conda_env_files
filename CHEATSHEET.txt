To make an environment from a file: 
	conda env create -f "RNAseq.yaml"
To make an enviornment:
	conda create --name "name-of-env"

To list all conda environments:
	conda env list

To move to a different conda environment:
	conda activate "name-of-env"

To remove a conda environment:
	conda remove --name myenv --all

To give jupyter a conda env install set
	python -m ipykernel install --user --name tensorflow --display-name "Python 3.8 (tensorflow)"

To update a conda env with a newer yml
	activate your env
	conda env update -f environment.yml

To export your current env to yml file
	conda env export > environment.yml
If you want a more succinct version (note doesn't keep channels?)
	conda env export --from-history > environment.yml



To allow for nicer running of R-code in JupyterLab
https://stackoverflow.com/questions/56460834/how-to-run-a-single-line-or-selected-code-in-a-jupyter-notebook-or-jupyterlab-ce
This seems like a healful way to create an Rstudio like python kernal.

```Settings --> Advanced Settings Editor --> JSON Settings Editor```
then copy and paste this:
```
{
            "command": "notebook:run-in-console",
            "keys": [
                "Ctrl Shift Enter"
            ],
            "selector": ".jp-Notebook.jp-mod-editMode"
},
```

To give jupyter an R conda env follow
	potentially to add R kernels: https://stackoverflow.com/questions/68939097/how-to-use-different-versions-of-r-kernels-in-vs-code-jupyter-notebooks-when-usi
  1. Make a conda env and get r-base
  2. activate the environment
  3. CD into `~/.local/share/jupyter/kernels` and make a new directory with the same name as your conda env
  4. Create a file called `kernel.json` 
  ```
  {"argv": 
          ["/SRA_store/shared/tools/mkozubov/miniconda3/envs/pcst/bin/R",
           "--slave",
           "-e",
           "IRkernel::main()",
           "--args",
           "{connection_file}"],
   "display_name":"Cytotalk-R 4.2.0",
   "language":"R"
  }
  ``` fill the file with this, and make the R path the path to a specific conda R you want, and change the Cytotalk display name. 
  5. Make sure that the conda env, PCST in my case, has the irkernel conda installed otherwise the kernel just wont connect!

