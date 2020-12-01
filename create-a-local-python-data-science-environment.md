# Create a Data Science Python Environment

If you've been curious about managing local Python environments for Data Analysis or Data Science, this short tutorial is for you. You’re going to install `Anaconda`, `conda`, and `ipykernel`, and by the end of this tutorial, you will know how to:

- Install Anaconda, Conda, and Jupyter Notebook
- Create a Conda virtual environment
- Install packages for your Conda virtual environment
- Install ipykernel for your Jupyter Notebook projects
- Activate and deactivate your Conda virtual environment
- Export your setting for sharing and collaboration with your team

In this tutorial, we'll install a local Python Data Science environment from scratch. I will use my new Macbook Pro 13" 2020, which uses the `zsh` shell by default. Windows users should follow Anaconda's installation instructions, but everything else should be the same(ie. if you use something like Powershell). Let's get started!

## So why not use pip and be done with it?

Great question, and here's why: pip does not have data science libraries pre-installed while other package managers, such as Anaconda, do. Another reason is collaboration-- sharing the same packages and versions can be tedious when you have one environment containing all of your libraries on one machine. There are many other reasons, such as faster performance, which are outside of scope for this tutorial.

Pip has a virtual environment called virtualenv, which has been replaced by pipenv, but they also doesn't contain the data science libraries that Anaconda has pre-installed. If you guessed that we're going to use Anaconda, you're right, and we're also going to use Anaconda's virtual env, aptly named `conda`. Let's begin by installing Anaconda!

## Install Anaconda

What is Anaconda? According to [WikiPedia](<https://en.wikipedia.org/wiki/Anaconda_(Python_distribution)>), Anaconda is a conditional free and open-source distribution of the Python and R programming languages for scientific computing that aims to simplify package management and deployment. The distribution includes data-science packages suitable for Windows, Linux, and macOS.

Anaconda comes bundled with almost everything that you would need to start your data science journey—from Python, Pip, Pandas, Numpy, Matplotlib, and more. Anaconda is a quick way to get started with data science because you won’t need to worry about installing the packages separately. However, you can still install packages manually via Pip with the `pip install` command.

> Note: Installing `Anaconda` means you will be using a minimum of 3 Gb of your disk space. That said, you can also install `miniconda` means you will be using around 400 Mb. That's the main difference between `Anaconda` and `miniconda`. In this tutorial, we will use Anaconda. Select your os below and follow the installation instruction:

- [Mac](https://docs.anaconda.com/anaconda/install/mac-os/)
- [Windows](https://docs.anaconda.com/anaconda/install/windows/)
- [Linux](https://docs.anaconda.com/anaconda/install/linux/)

Congratulations, your python data science environment has been successfully setup!

## Create and export your Virtual Environment

Now that you have Anaconda installed, crate a new project folder. Next, `cd` into your project folder directory, then set-up your virtual environment with the following command:

```bash
# Go to the folder of your project
$ cd your_project_folder
```

For example, my project is `excelProject`, and where I will use `python=3.8` and install the `notebook pandas matplotlib seaborn` packages. To specify your prefered python version and any packages you may want to use, enter the following command:

```bash
# Install virtualenv
conda create --name excelProject python=3.8 notebook pandas matplotlib seaborn
```

After you create your conda environment, you can activate your environment:

```bash
# Activate excel
$ conda activate excelProject
```

To deactivate:

```bash
# Deactivate excel
$ conda deactivate
```

To view your conda virtual environments, you have created or have available on your machine, us this command:

```bash
# List all virtual environments
conda env list
```

You can also save and share your virtual environment:

```bash
# Share this environment
conda env export > environment.yml

# Spawn this environment
conda env create -f environment.yml
```

To remove the virtual environment:

```bash
# Remove the virtual environment
conda env remove -n myenv
```

## Jupyter Notebook Kernel

Before we can start using our virtual env, it's important to note that our new conda virtual environment is not using the same kernel as our new virtual environment; it's using the system kernel. The system kernel is not what we want; we want to use the virtual environment kernel that we created.

To verify this, you can open Jupyter Notebook where you won't see our new virtual environment kernel as an option to create a new notebook:

`jupyter notebook`

Solution:
To get the correct kernel to display as an option in Jupyter notebooks, install `ipykernel` inside of your active virtual environment session. Our active session shows up as (excelProject) in the terminal. Once you verify that you are in the correct directory using an active session, use this command:

`pip install ipykernel`

Next, install ipykernel to the conda env, like this:

```
python -m ipykernel install --user --name excelProject --display-name "excelProject"
```

Open a new Jupyter Notebook session:

```bash
# Open Jupyter Notebook
jupyter notebook
```

As you can see, you now have the correct kernel as an option to create a new notebook. We can even test out our new kernel by creating a new Jupyter Notebook then use this command:

```bash
# Show conda virtual environments
conda env list
```

To view your Jupyter notebook kernels:

```bash
jupyter kernelspec list
```

To remove the kernel associated with your virtual environment:

```bash
# Remove kernel from the virtual environment
jupyter kernelspec uninstall myenv
```

> Note: you may need to restart the kernel to use updated packages.

I hope you enjoyed this tutorial and feel excited about learning Python. If you have any suggestions or mistakes to report, feel free to crate a ticket [HERE](https://github.com/jonathan-barrios/python-data-science-environments/issues/new/choose). Keep going and, and as always, happy analyzing! 🙌🏼
