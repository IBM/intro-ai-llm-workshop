# Agentic AI with Open-WebUI

LLM Models are only as good as the data they're trained on.  But what if you want current information from the web? The LLM model could be 6-months or a year behind on current events or weather, sport team results, etc. As you saw in lab-4, one solution is to add a RAG document with the latest data/information you're interested in, and it'll get used in the answer. But another way is to use Agentic AI where the AI solution could reach out to the web to do a web crawl and get the latest information for you.  To do that, we need the following:

5.1 We need these models downloaded to your Ollama server:
```bash
ollama pull granite3.3:8b
ollama pull granite3.3:2b
ollama pull granite-embedding:278m
```

5.2 Make sure you're started up and are in your python environment:
=== "Windows"
    1. From a command prompt, run the following command to activate your virtual environment:
       ```shell
       "venv/Scripts/activate.bat"
        ```

=== "MacOS"
    1. From a terminal window, run the following command to activate your virtual environment:
       ```shell
       source .venv/bin/activate
        ```

5.3 In your python environment, we need to install these 3 python packages:
```bash
pip install gpt-researcher
pip install langchain_ollama
pip install duckduckgo_search 
```

5.4 In your Open-WebUI browser window:
5.4.1 Click on the circle with your initial on the far right of the screen and select "Admin Panel."
5.4.2 Click on the "Functions" tab at the top
5.4.3 Click on the "+" button to create an Search Agent function
5.4.4 Give it a name:  For example: Searcher
5.4.5 Give it a Description:  For example: Searcher-AI
5.4.6 Paste in this code:
```shell
"""
title: Researcher Agent Pipe
author: yihongwang@gmail.com
date: 2025-040-8
version: 0.1
license: MIT
description: Enable the gpt-researcher using Granite models via Ollama by default.
             Modify valve settings if you use different models/API.
             Be sure to update the `OLLAMA_BASE_URL` to point to your Ollama server.
requirements: gpt-researcher, langchain_ollama, duckduckgo-search
"""

from pydantic import BaseModel, Field
import asyncio
import json
import os
import sys
from gpt_researcher import GPTResearcher


class Pipe:
    class Valves(BaseModel):
        FAST_LLM: str = Field(default="ollama:granite3.3:2b")
        SMART_LLM: str = Field(default="ollama:granite3.3:8b")
        STRATEGIC_LLM: str = Field(default="ollama:granite3.3:8b")
        EMBEDDING: str = Field(default="ollama:granite-embedding:278m")
        OLLAMA_BASE_URL: str = Field(default="http://localhost:11434")
        OPENAI_API_KEY: str = Field(default="ollama")

    def __init__(self):
        self.valves = self.Valves()

    async def pipe(self, body: dict):
        print(body["messages"][-1]["content"])
        os.environ["FAST_LLM"] = self.valves.FAST_LLM
        os.environ["SMART_LLM"] = self.valves.SMART_LLM
        os.environ["STRATEGIC_LLM"] = self.valves.STRATEGIC_LLM
        os.environ["EMBEDDING"] = self.valves.EMBEDDING
        os.environ["OPENAI_API_KEY"] = self.valves.OPENAI_API_KEY
        os.environ["OLLAMA_BASE_URL"] = self.valves.OLLAMA_BASE_URL
        os.environ["RETRIEVER"] = "duckduckgo"
        os.environ["LLM_KWARGS"] = json.dumps({"num_ctx": 1024 * 128})
        researcher = GPTResearcher(
            query=body["messages"][-1]["content"],
            report_type="research_report",
        )
        research_result = await researcher.conduct_research()
        report = await researcher.write_report()

        # Get additional information
        research_context = researcher.get_research_context()
        research_costs = researcher.get_costs()
        research_images = researcher.get_research_images()
        research_sources = researcher.get_research_sources()
        print("Report:")
        print(report)
        print("\nResearch context:")
        print(research_context)
        print("\nResearch Costs:")
        print(research_costs)
        print("\nNumber of Research Images:")
        print(len(research_images))
        print("\nNumber of Research Sources:")
        print(len(research_sources))
        return report
```

### 5.5 In the Open-WebUI, switch to use your "Searcher" function rather than one of the Ollama models.

### 5.6 Ask your question, for example:
```shell
Tell me the weather today in San Jose California

or

What is the last result of the San Franicisco Giants game?
```

After about 10 minutes, it should have scraped the result from the web and pasted it in the Open-WebUI.

