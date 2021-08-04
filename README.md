# build-ortho2align
conda recipe for building ortho2align.

## How to build and upload the package
1. Run the following commands to build the package.
    ```{bash}
    conda activate buildenv
    conda-build .
    ```
2. Save a path to the built package and navigate to those directory.
    ```{bash}
    cd PACKAGE_PATH
    ```
3. Upload linux-64 packages to Anaconda.
    ```{bash}
    anaconda upload ortho2align-VERSION-PYVERSION.tar.bz2
    ```
4. Convert the package to osx-64.
    ```{bash}
    cd ..
    conda convert --platfrom osx-64 linux-64/ortho2align-VERSION-PYVERSION.tar.bz2 -o osx-64
    ```
5. Upload osx-64 packages to Anaconda.
    ```{bash}
    cd osx-64
    anaconda upload *
    ```
6. Clean build intermediates.
    ```{bash}
    conda build purge
    ```

## How to test package
1. Prepare test environment.
    ```{bash}
    conda activate testenv
    conda remove ortho2align
    conda clean --all
    ```
2. Install the latest version of the package.
    ```{bash}
    conda install -c dmitrymyl ortho2align
    ```
3. Follow testing instructions in [ortho2align repo](https://github.com/dmitrymyl/ortho2align#testing).