# Pre-work

Assumptions:

These labs can be run on a Windows 11 or MacOS machine.
Click on the operation system you are using below to get the
corresponding instructions.

### Ollama Installation
=== "Windows"
    1.  Download [Ollama for Windows](https://ollama.com/download/windows)

    1.  Install Ollama by double-clicking on the downloaded `OllamaSetup.exe`
        And then clicking on "Install"

    1.  In a CMD or terminal window, pull down the Granite models you will want to use in the workshop. Larger models take more memory to run but can give better results.  It will take time to download the bigger models depending on your network speed.
	```
	ollama pull granite3.3:2b
	ollama pull granite3.2-vision:2b
	ollama pull granite3.3:8b
	```

	Note: We won't use them for this lab, but if you wanted to try some other LLM models, you can start with:
	```
	ollama pull deepseek-r1:1.5b
	ollama pull llama3.2:3b
	```
	Check out the entire Hugging face library of models at: https://ollama.com/library

=== "MacOS"
    1.  Download [Ollama for Mac](https://ollama.com/download/Ollama.dmg)

    1.  Drag the Ollama to your applications folder, then double-click on the ollama application to start it up.

    1.  In a terminal window, pull down the Granite models you will want to use in the workshop. Larger models take more memory to run but can give better results.  It will take time to download the bigger models depending on your network speed.
        ```
        ollama pull granite3.3:2b
        ollama pull granite3.2-vision:2b
        ollama pull granite3.3:8b
        ```

        Note: We won't use them for this lab, but if you wanted to try some other LLM models, you can start with:
        ```
        ollama pull deepseek-r1:1.5b
        ollama pull llama3.2:3b
        ```
        Check out the entire Hugging face library of models at: https://ollama.com/library

### Install Python
For the workshop you will need Python 3.11.9. Follow the steps below for your operating system:

=== "Windows"
    1.  Download the Python [python-3.11.9-amd64.exe](https://www.python.org/ftp/python/3.11.9/python-3.11.9-amd64.exe)

    1.  Double-click to install it

        !!! note
            While installing - make sure you check the box to "add the python.exe to path"**

    1.  Close and re-open your command prompt and then check to make sure python is findable on the path by typing:
        ```shell
        python --version
        ```
        It should return: "Python 3.11.9"

    !!! note
        If it doesn't find the python command, likely you forgot to check the box to put python in the path.  No worry, just:

        1.  Double-click on the downloaded python-3.1.9-amd64.exe file again and this time chose "Modify" and click "next" 
        1.  Put a check next to the box: "Add Python to the environnment variables" and click "Install".

    1.  Optionally, you can also download and install git from [git-scm.com/downloads](https://git-scm.com/downloads/win)  

        1. The latest one as of writing this document is: [Git-2.49.0-64-bit.exe](https://github.com/git-for-windows/git/releases/download/v2.49.0.windows.1/Git-2.49.0-64-bit.exe)
        1. Double-click on the downloaded Git-2.49.0-64-bit.exe, take all the defaults and install

=== "MacOS"
    1.  Open a terminal window and check to see if you have the brew command already:
        ```shell
        brew
        ```

    1.  If you have Brew, skip to the next step.  Otherwise, install brew on MacOS with this command:
        ```shell
        /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
        ```
  
    1.  Install uv for MacOS. If you don't have them already:
        ```shell
        brew update
        brew install uv
        ```

    1.  Install Python 3.11.9 for MacOS
        ```shell
        uv venv --python 3.11 --seed .venv
        ```

    1.  Activate the Python virtual env you just created:
        ```shell
        source .venv/bin/activate
        ```

    1. Verify the Python version:
        ```shell
        python --version
        ```
        It should return now 3.11.x

### Python Virtual Environment:

Python virtual environment is used to isolated Python installations. Let's create one called "venv" and
use it for the workshop.

=== "Windows"
    1.  Open the command prompt run the following command to create a new virtual environment:
        ```shell
        python -m venv --upgrade-deps --clear venv
        ```

    1.  Activate your python environment by typing:
        ```shell
        "venv/Scripts/activate.bat"
        ```

=== "MacOS"
    1.  Open up a terminal window and install Python 3.11.x for MacOS which also creates a python virtual environment
        ```shell
        uv venv --python 3.11 --seed .venv
        ```
        
    1.  Activate the Python virtual env you just created:
        ```shell
        source .venv/bin/activate
        ```

    1. Verify the Python version:
        ```shell
        python --version
        ```
        It should return now 3.11.x

### Install the Open-WebUI
=== "Windows"
    1.  In the open command prompt, run the following command to Install the Open-WebUI:
        ```shell
        pip install open-webui
        ```

=== "MacOS"
    1.  In the open terminal window, run the following command to Install the Open-WebUI:
        ```shell
        uv pip install open-webui 
        ```

1.  Start up open-webui. You will leave this running during the workshop.
    ```shell
    open-webui serve
    ```

### Access Open-WebUI

1.  Once the open-webui starts, use a browser to login to open-webui:
    [http://localhost:8080](http://localhost:8080)

1.  Enter a name, email address and password - these are stored locally. (Don't forget them!) 

### Create scripts to activate and start your environments up with one "go-webui" script going forward:
=== "Windows"
    1.  In a command prompt, type in "notepad go-webui.bat" and press enter, then add the following info and press save:
        ```shell
        @echo off
        CALL "%USERPROFILE%\venv\Scripts\activate.bat"
        open-webui serve
        ```

    1.  Run the bat script from the command line in the future by typing:
        ```shell
        go-webui.bat
        ```

=== "MacOS"
    1.  Open a terminal window and run the following commands to create a go-webui.sh shell script:
        ```shell
        echo "source .venv/bin/activate" > ~/Desktop/go-webui.command
        echo "open-webui serve" >> ~/Desktop/go-webui.command
        chmod +x ~/Desktop/go-webui.command
        ```
    1.  Run the shell script from a terminal window in the future by typing:
        ```shell
        ~/Desktop/go-webui.command/go-webui.command
        ```

        Or you can doubleclick on the go-webui.command window on your Desktop


## Cleaning up after the lab is complete:

1.  Remove all the models you don't want:
    ```shell
    ollama list
    ollama rm granite3.3:2b granite3.3:8b granite3.2-vision:2b
    ```

1. Uninstall ollama:

    === "Windows"
        In the search bar, search for Settings --> Apps --> Installed Apps and search for Ollama and click on Uninstall

    === "MacOS"
        In a terminal, use `brew` to uninstall `ollama`:
        ```shell
        brew uninstall ollama
        ```
  
        Or if you dragged Ollama to the applicatino folder, you can delete the Ollama application in the Application folder.

1. Stop and remove open-webUI:

    === "Windows"
        1.  In the command line where open-webui is running, do a ctrl-C to stop the "open-webui serve"

        1.  Deactivate your python environment session by typing: 
            ```shell
            venv/Scripts/deactivate.bat
            ```
        
        1.  If you want to remove the virtual environment completely:
            ```shell
            rmdir /s venv
            ```

    === "MacOS"
        1.  In the command line where open-webui is running, do a ctrl-C to stop the "open-webui serve"
        1. Deactivate your python environment session by typing: 
            ```shell
            deactivate
            ```
        1.  If you want to remove the virutal environment completely:
            ```shell
            rm -rf venv
            ```

