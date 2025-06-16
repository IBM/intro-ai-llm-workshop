# Command-Line Ollama
Ollama provides a CLI tool to interact with large language models. In this lab, you will learn how to use it
to run the IBM granite models and get answers to some questions.

You will need the Windows `Command Prompt` or the `Terminal` in the MacOS to run the Ollama CLI in this lab.

### List the available models downloaded
Use the following command to list the models in your current system.
```bash
ollama list
```

### Try `granite3.3:2b` Model

1.  Use `ollama run` command and specify the model name to run a model and start the
    conversation. Let's try out the `granite3.3:2b` model.:
    ```bash
    ollama run granite3.3:2b
    ```
    You will see the prompt like this:
    ```bash
    >>> Send a message (/? for help)
    ```

1.  Ask some questions to the model. Here are some examples:
    ```bash
    What is the difference between a mammal and a reptile? Provide examples for each.
    ```
    ```bash
    Create an easy to make chocolate chip cookie recipe
    ```
    ```bash
    Who was Marie Curie and what are her key discoveries in the field of chemistry and physics?
    ```
    Hit `<Enter>` key when you finish your question and you will see the model start to reply your question. For example:
    ```base
    >>> What is the difference between a mammal and a reptile? Provide examples for each.
    Mammals and reptiles are both distinct groups of animals within the animal kingdom, differing in several key characteristics, including their body coverings, reproduction strategies, and warm-bloodedness. Here's a detailed comparison with examples for each:

    1. Body Covering:
    - Mammals: They have smooth, hairy, or scaly skin (depending on the species). Their young are born alive and nourished by milk through mammary glands. Examples include humans, dogs, cats, cows, and dolphins.
    - Reptiles: They are covered with scales for protection and water conservation. Their young hatch from eggs, unlike mammals that give live birth or lay eggs like birds. Examples include snakes, lizards, turtles, and crocodiles.

    2. Reproduction Strategy:
    - Mammals: Most mammals exhibit internal fertilization (egg within the parent's body) and nurse their young with milk. Examples include humans (milk-producing mammary glands), pigs, horses, and whales.
    - Reptiles: Typically lay eggs externally, and the development of embryos occurs without nourishment from a mother's body. Examples include sea turtles, alligators, and most lizards.

    3. Warm-bloodedness (Endothermy):
    - Mammals: They maintain a stable internal body temperature regardless of external conditions through thermogenesis (heat production). Examples include humans, dogs, cats, and polar bears.
    - Reptiles: Most reptiles are ectothermic, meaning they rely on external sources like sunlight to regulate their body temperature. This allows them to adapt to diverse habitats but makes them less efficient in colder environments. Examples include crocodiles, snakes,
    and turtles.

    4. Respiratory System:
    - Mammals: They possess lungs for gas exchange and use highly vascularized (well-developed network of blood vessels) systems for efficient oxygen uptake and carbon dioxide removal. Examples include humans, dogs, and rodents.
    - Reptiles: Some reptiles have lungs, while others employ other respiratory methods like skin respiration (exchange of gases through the skin). Crocodilians, for instance, rely on cutaneous (skin) respiration, allowing them to survive in oxygen-poor environments.

    In summary, mammals and reptiles differ significantly in their body coverings, reproductive strategies, thermal regulation, and respiratory systems. Mammals are warm-blooded, give birth to live young or lay eggs with mammary glands, and have sophisticated internal
    organs for efficient gas exchange. Reptiles, on the other hand, are ectothermic, lay eggs, and employ various respiratory methods adapted to their habitats.
    ```

1.  After you receive the response or answer from the model, you can ask the model to explain or refine the answer if you have further questions
    which are related to the first question or the response content. This is the concept of the `context`.

1.  To clear the context, you can use the `/clear` command. Then you can start a new conversation.
    ```bash
    /clear
    ```
    You will see the following message indecating the context is cleared:
    ```bash
    Cleared session context
    >>> Send a message (/? for help)
    ```

1.  Instructions for changing the behavior of the model:
    
    Give it clear instructions to change it's behavior.  For example:
    ```bash
    Answer questions from now on in Spanish
    ```
    ```bash
    Answer questions like a pirate
    ```

1.  Exit out of the current model
    ```bash
    /bye
    ```

### Try Another Model
Let's try out another model with more questions:

1.  List the available models in the system again:
    ```bash
    ollama list
    ```

1.  How about `granite3.2-version:latest` model:
    ```bash
    ollama run granite3.2-vision:latest
    ```
1.  Some example questions:
    ```bash
    Create an easy to make chocolate chip cookie recipe
    ```
    ```bash
    List the ingredients as well as 5 optional additions
    ```
1.  Exit out of the current model:
    ```bash
    /bye
    ```

