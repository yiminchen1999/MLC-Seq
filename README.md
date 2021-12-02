# MLC-Seq

### Description
the implementation of MLC-Seq algorithm

### Prepare the environment for Linux/MacOS
1. Download and install Python3, Python version 3.5+ is required. (https://www.python.org/downloads/)
2. Open the Terminal.
3. Create an virtual environment by the following command
```Bash
python3 -m venv <your_virtual_workspace_path>
```
For example, if the virtual environment path is "~/Downloads/vir_env", simply run
```Bash
python3 -m venv ~/Downloads/vir_env
```
4. Activate the virtual environment
```Bash
source <your_virtual_workspace_path>/bin/activate
```
For example, 
```Bash
source ~/Downloads/vir_env/bin/activate
```
5. Download this project(MLC-Seq), Usually you will download a zip file, just unzip it. Suppose you extract the project into your "Downloads" folder, you will get your project path "~/Downloads/MLC-Seq-main". Change to the directory of this project
```Bash
cd ~/Downloads/MLC-Seq-main
```
6. use the following command to install all the required libraries
```Bash
pip install -r requirements.txt
```

### Prepare the environment for Windows
1. Download and install Python3, Python version 3.5+ is required. (https://www.python.org/downloads/)
2. Open the Command Prompt(cmd.exe).
3. Create an virtual environment by the following command
```Bash
python3 -m venv <your_virtual_workspace_path>
```
For example, if the virtual environment path is "C:\vir_env", simply run
```Bash
python3 -m venv C:\vir_env
```
4. Activate the virtual environment
```Bash
<your_virtual_workspace_path>\Scripts\activate.bat
```
For example, 
```Bash
C:\vir_env\Scripts\activate.bat
```
5. Download this project(MLC-Seq), Usually you will download a zip file, just unzip it. Suppose you extract the project into "C:\" folder, you will get your project path "C:\MLC-Seq-main". Change to the directory of this project
```Bash
cd C:\MLC-Seq-main
```
6. use the following command to install all the required libraries
```Bash
pip install -r requirements.txt
```
### Launch the project
run the following command to launch the project, then the main page of MLC-Seq will be presented in your default browser.
```Bash
jupyter notebook
```

The folder <em>modules</em> includes the main tools and algorithms used in the project. The folder <em>samples</em> has three sub-folders. They are the deconvoluted results(Data sources of our algorithms.) for tRNA-Phe, Glu, and Gln. The folder <em>examples</em> contains several notebooks (.ipnyb) that illustrate the usage of MLC-Seq algorithms in different levels. The notebook trna_phe_analysis.ipynb presents the data processing using tRNA-Phe as an example. The notebook trna_phe_analysis_lite.ipynb is a short version for users who don't have much time to explore the algorithm, you can run the notebook and get a rough result in 1 minute.