# README

Contains a default repo for python-based spatiotemporal data analyses using `pixi` as the package manager. I like pixi (over `uv`, for example) because it is really good at handling dependences for a mix of conda and pip packages. 

# Usage

1. Clone this repo (or use it as a template using github's template repo feature)

2. Rename the project to whatever you'd like, by replacing the folder name in `/src/template_workflow` to whatever you'd like the name to be. Also, open up `pyproject.toml` and replace the two instances of `template_workflow` -- one should be at the top of the file in the `[project]` section, and the other should be in the `[tool.pixi.pypi-dependencies]` section.

3. install pixi, if you haven't already. On linux/mac, running this command in the terminal should do the trick: `curl -fsSL https://pixi.sh/install.sh | sh`

4. In the terminal, `cd` your way into the project directory (i.e., where the pyproject.toml and pixi.lock lives), and run `pixi install`. 

5. Start coding! 

- If you use vscode/positron, you should be able to see the newly added python installation when you go to select interpreters (you might need to cmd-shift-p and run "Interpreter: Discover all interpreters"). 

- If you use jupyterlab, then you can run `pixi shell` in terminal, and then run `jupyter lab`. (note: `pixi shell` is similar to `conda activate`). 

    - In a notebook, you might want to add the lines `%load_ext autoreload` and `%autoreload complete`. This will automatically reload the local project code whenever you make changes to the `src` files.

- My general workflow is to throw in helper functions / shared preprocessing steps inside the `src/template_workflow` folder, and then do one-off analyses / figure generation / summaries in the `notebooks` folder. Check out the example notebook to see how to use the helper functions. 

6. (as needed) Add packages. A handful of packages have already been added (see the `pyproject.toml`), but to add more, you can run `pixi add ____`, where the name of the package goes inside the blank. By default, it'll use conda-forge to grab the packages, but you can also add pip packages by adding a flag (see the pixi documentation for details)

7. Whenever you make changes to the project, make sure you track changes in the pixi.lock and pyproject.toml! This is the secret sauce that makes everything reproducible. Do not track changes in the `.pixi` folder (there's already a .gitignore in there, so you shouldn't have to worry about it.)

# How this repo was created

```
pixi init --format pyproject
pixi add python numpy gdal libgdal-core rasterio dask netcdf4 h5netcdf pyogrio cartopy xarray regionmask
pixi workspace platform add osx-arm64 win-64 linux-64
```

