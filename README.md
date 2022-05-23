# MLC-Seq

## Description
The implementation of **MLC-Seq** algorithm to direct sequence RNA.

## System Requirements

### Hardware requirements
**MLC-Seq** requires only a standard computer with enough RAM to support the in-memory operations.

### Software requirements
#### OS requirements
This project is supported for macOS/Linux and Windows. The project has been tested on the following systems:
macOS: Big Sur (11.1)
Windows: Windows 10

### Python dependencies
1. Python version 3.5+ is required. Go to https://www.python.org/downloads/ to download python and follow the instruction for installation.
2. The rest dependencies are listed inside requirements.txt, please refer to the Prepare the Environment section on how to install them. They should install in about 2 minutes, depending on your network speed.

## Download
Clone this repository. Click the green button "Code" and click the "Download ZIP" button. Now a zip file named "MLC-Seq-main.zip" is downloaded. Unzip this file. In macOS/Linux system, usually the path of the project is ~/Downloads/MLC-Seq-main. In Windows system, suppose the path of the project is C:\MLC-Seq-main.

## Prepare the Environment
Environment preparation for macOS/Linux and Windows will be described separately.
### Prepare the environment for macOS/Linux
1. Open the Terminal.
2. Create an virtual environment by entering the following command
```Bash
python3 -m venv <your_virtual_workspace_path>
```
To make it simple, we can setup the virtual environment "vir_env" in "Downloads" folder by entering the command
```Bash
python3 -m venv ~/Downloads/vir_env
```
3. Activate the virtual environment
```Bash
source <your_virtual_workspace_path>/bin/activate
```
In our case, enter the command
```Bash
source ~/Downloads/vir_env/bin/activate
```
4. Go to the root directory of MLC-Seq project and install all the required libraries. Enter the command
```Bash
cd <root_directory_path>
pip install -r requirements.txt
```
In our case, enter
```Bash
cd ~/Downloads/MLC-Seq-main
pip install -r requirements.txt
```

### Prepare the environment for Windows
1. Open the Command Prompt(cmd.exe).
2. Create an virtual environment by entering the following command
```Bash
python3 -m venv <your_virtual_workspace_path>
```
Similarly, we can setup the virtual environment "vir_env" in C drive by entering the command
```Bash
python3 -m venv C:\vir_env
```
3. Activate the virtual environment
```Bash
<your_virtual_workspace_path>\Scripts\activate.bat
```
In our case, enter the command 
```Bash
C:\vir_env\Scripts\activate.bat
```
4. Go to the root directory of the project MLC-Seq and install all the required libraries. Enter the command
```Bash
cd <root_directory_path>
pip install -r requirements.txt
```
In our case, enter
```Bash
cd C:\MLC-Seq-main
pip install -r requirements.txt
```
## Launch the Project
Run the following command to launch the project, then project **MLC-Seq** will be located in your default browser.
```Bash
jupyter notebook
```

The main page of MLC-Seq is now presented in your default browser. We will be processing the data in this window.

## Project Structure Description
- The folder <em>**modules**</em> includes the main tools and algorithms used in the project. 
- The folder <em>**samples**</em> has three sub-folders. They are the deconvoluted results (data sources of our algorithms.) for tRNA-Phe, Glu, and Gln. 
- The folder <em>**examples**</em> contains several notebooks (.ipnyb) that illustrate the usage of **MLC-Seq** algorithms in different levels. 

	- The notebook <em>**trna_phe_analysis_lite.ipynb**</em> is a simplified version of data processing, using one of the isoforms of <em>tRNA-Phe</em> as an example. After further selelction (described in method section), the result is then used for ladder complementation.The notebook <em>**trna_phe_analysis.ipynb**</em> presents the data processing using <em>tRNA-Phe</em> as an example. 
	- The notebook <em>**trna_phe_analysis.ipynb**</em> presents the data processing using <em>tRNA-Phe</em> as an example.

## Demo Videos
- [This video](https://youtu.be/0hQkDnjLPZM) shows how to install this project.
- [This video](https://youtu.be/pliz7t1gWKg) demonstrates how to run the notebook <em>**trna_phe_analysis_lite.ipynb**</em>.
- [This video](https://youtu.be/eyJBcZLqakg) shows how to run the notebook <em>**trna_phe_analysis.ipynb**</em>, change parameters for the purpose of obtaining more results.

