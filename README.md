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
5. Download this project(MLC-Seq), Usually you will download a zip file, just unzip it. Suppose you extract the project into your "Downloads" folder(Linux/MacOS), you will get your project path "~/Downloads/MLC-Seq" or "C:\MLC-Seq", Go to the root directory of this project
```Bash
cd ~/Downloads/MLC-Seq
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
For example, if the virtual environment path is "C:\vir_env"(Windows), simply run
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
5. Download this project(MLC-Seq), Usually you will download a zip file, just unzip it. Suppose you extract the project into "C:\" folder, you will get your project path "C:\MLC-Seq", Go to the root directory of this project
```Bash
cd C:\MLC-Seq
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

Now we are in jupyter and the main page of MLC-Seq is presented in your default browser. We will be processing the data in this window. "modules" includes main tools and algorithms used in the project. "samples" has 3 folders, they are the deconvoluted results for tRNA-Phe, Glu and Gln. "examples" has one application (.ipnyb) and two excel sheets. The application of trna_phe_analysis.ipynb presents the data processing using tRNA-Phe as an example. The two excel sheets are the rough data for 5´ and 3´-end used in the application.