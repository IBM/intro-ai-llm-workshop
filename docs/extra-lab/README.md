# Retrieval-Augmented Generation (Extra lab)

### 1.1 In the Open-WebUI, switch to the smallest Granite model: granite3.3:2b
```bash
granite3.3:2b
```

### 1.2 Click on "New Chat" so the context is clear

### 1.3 Ask it for:
```bash
List the past and current CEOs of the IBM corporation from first to last.
```
The answer isn't correct.

### 1.4 Click on "New Chat" to clear the context

### 1.5 Download a small text file with the correct list of IBM CEOs to your Downloads folder:
[IBM.txt](https://ibm.github.io/intro-ai-llm-workshop/resources/IBM.txt)

### 1.6 Click on the "+" and then Upload files

Upload the IBM.txt file that you just downloaded

### 1.7 Now ask it our question about the CEOs of IBM:
```bash
List all the past and current CEOs of the IBM corporation from first to last.
```
The answer should now be correct. (For example, always before it forgets Jon Akers)

### 1.8 We can also find and download information to pdf from Wikipedia:
For example: [History of IBM](https://en.wikipedia.org/wiki/History_of_IBM)

### 1.9  On the right, click on "Tools" and Click on "Download as PDF"

### 1.10 Then use this History_of_IBM.pdf as a RAG by clicking on the + and adding "History_of_IBM.pdf" as a file.

### 1.11 Then use the Open-WebUI to ask more questions about IBM.
```bash
Who is the first female CEO of IBM?
```
The answer should be Ginni Rometty
