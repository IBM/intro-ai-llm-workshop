# Command-Line Ollama

## 1.1 List the available models downloaded
```bash
ollama list
```
## 1.2 Run one of the models, for example:
```bash
ollama run granite3.3:2b
```
## 1.3 Issue it some questions, try it out.  For example:
```bash
What is the difference between a mammal and a reptile? Provide examples for each.
```
```bash
Create an easy to make chocolate chip cookie recipe
```
```bash
Who was Marie Curie and what are her key discoveries in the field of chemistry and physics?
```
## 1.4 Clear the context
```bash
/clear
```
## 1.5 Give it clear instructions to change it's behavior.  For example:
```bash
Answer questions from now on in Spanish

Answer questions like a pirate
```
## 1.6 Exit out of the current model
```bash
/bye
```
## 1.7 List and then start another model:
```bash
ollama list
ollama run granite3.2-vision:latest
```
## 1.8 Issue it some questions, try it out.  For example:
```bash
Create an easy to make chocolate chip cookie recipe
```
```bash
List the ingredients as well as 5 optional additions
```
## 1.9  Exit out of the current model:
```bash
/bye
```

