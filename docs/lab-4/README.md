# Graphics and MultiModal LLM

4.1 Get into the python environment if you're not already there:
4.2 Start the Open WebUI
```bash
open-webui serve
```
4.3 Hit the localhost with the browser:
        http://localhost:8080/
4.4 Pick a model to use, for example:
        granite3.2-vision:2b
4.5 Issue it some questions, try it out.  For example:
```bash
list the first 10 presidents of the united states
create an easy to make chocolate chip cookie recipe
```
4.6 Clear the context by clicking on "New Chat"
4.7 Using another tab on the browser, search for a image.  For example:
```bash
Kangaroo
```
4.8 In the Google search, click on the "Images" tab and right-click on one of the photos you like and select "Copy Image"
4.9 Using the Open-WebUI browser, do a `CTRL-V` to paste the copied image to the Open-WebUI and press enter. The Granite vision model will summarize what it sees from the image.
4.10 Go ahead and ask the AI more questions about the animal in the image.  For example:
```bash
What is the lifespan for the animal in the photo?
```
