# Pre-work

Assumptions:

These labs assume you have a Microsoft Windows 11 machine

1.1 Download and Install Ollama:
https://ollama.com/download/windows
Install Ollama by double-clicking on: OllamaSetup.exe

1.2 Open up a command prompt (Search for "CMD" and click on "Command Prompt")

1.3. Download at least 3 of the Granite models
```shell
ollama pull granite3.3:2b
ollama pull granite3.2-vision:2b
ollama pull granite3.3:8b
```
Note: We won't use them for this lab, but if you wanted to try some other LLM models, you can start with:
```shell
ollama pull deepseek-r1:1.5b
ollama pull llama3.2:3b
```
Check out the entire Hugging face library of models at: https://ollama.com/library

1.4 Install Python 3.11
	https://www.python.org/ftp/python/3.11.9/python-3.11.9-amd64.exe
	Double-click to install it
**Note: While installing - make sure you check the box to "add the python.exe to path"**

1.5 Close and re-open your command prompt and then check to make sure python is findable on the path by typing:
```shell
python --version
```
It should return: "Python 3.11.9"

1.6 Create a python virtual environment in your command prmopt:
```shell
python -m venv --upgrade-deps --clear venv
```

1.7 Activate your python environment by typing:
```shell
"venv/Scripts/activate.bat"
```

1.8 Upgrade your pip version:
```shell
python -m pip install --upgrade pip
```

1.9 Install the Open-WebUI
```shell
pip install open-webui
```

1.10 Start up open-webui:
```shell
open-webui serve
```

1.11 Once the open-webui starts, use a browser to login to open-webui:
http://localhost:8080

Enter a name, email address and password - these are stored locally.

# Cleaning up after the lab is complete:

Remove all the models you don't want:
```shell
ollama list
ollama rm granite3.3:2b granite3.3:8b granite3.2-vision:2b
```

Uninstall ollama:

In the search bar, search for Settings --> Apps --> Installed Apps and search for Ollama and click on Uninstall

Stop and remove open-webUI:

In the command line where open-webui is running, do a ctrl-C to stop the "open-webui serve"

Then, type 
```shell
"venv/Scripts/deactivate.bat" to exit the python virtual environment
```
If you want to remove the virutal environment completely, you could issue a:
```shell
rmdir /s venv
```


