# Mac Instructions to install Ollama and Open-WebUI

Assumptions:

These instructions assume you have a MacOS machine.  

## 1.1 Download and Install Ollama for MacOS:

On macOS, you can use Homebrew to install with:

```shell
brew install ollama
```

## 1.2 Start the Ollama server. You will leave this running during the workshop.
```shell
ollama serve
```

## 1.3 In another terminal window, pull down the Granite models you will want to use in the workshop. Larger models take more memory to run but can give better results.
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

## 1.4 Install Python 3.11.9 for MacOS
```shell
pyenv install 3.11
```
```shell
pyenv global 3.11.9
```

```shell
pyenv -V
```
It should return now 3.11.9

## 1.5 Create a Python virtual environment:
```shell
python3 -m venv --upgrade-deps venv
```
## 1.6 Activate the virtual environment:
```shell
source venv/bin/activate
```
## 1.7 Install Open-WebUI
```shell
pip install open-webui
```
## 1.8 Start up Open-WebUI in a terminal window. You will leave this running during the workshop.
```shell
open-webui serve
```
