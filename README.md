# ollama-llm

This project shows how to run Ollama's models, including the `mistral` model, in Google Colab. The setup uses `colab-xterm` to access a terminal within Colab and integrates with Ollama models using `langchain-ollama`.

### Steps to Get Started:

1.  **Open a Terminal in Colab**:

    -   First, you need to install and load the `colab-xterm` extension to use a terminal in Colab. Run these commands:

        python

        Copy code

        `!pip install colab-xterm
        %load_ext colabxterm
        %xterm`

2.  **Install Ollama**:

    -   Once the terminal is active, you can install Ollama by running this command:

        bash

        Copy code

        `curl https://ollama.ai/install.sh | sh`

3.  **Download the `mistral` Model**:

    -   After installing Ollama, start the Ollama server and pull the `mistral` model:

        bash

        Copy code

        `ollama serve &
        ollama pull mistral`

4.  **Verify the Model**:

    -   Check if the model has been installed correctly by running the following:

        bash

        Copy code

        `!ollama list`

5.  **Install `langchain-ollama`**:

    -   Finally, install the `langchain-ollama` package to connect with Ollama models:

        python

        Copy code

        `%pip install -U langchain-ollama`

### How to Use the Model:

After setting everything up, you can use the model to generate responses to questions.

Here's a sample code you can run:

python

Copy code

`from langchain_core.prompts import ChatPromptTemplate
from langchain_ollama.llms import OllamaLLM

# Define the prompt template
template = """Question: {question}

Answer: Let's think step by step."""

prompt = ChatPromptTemplate.from_template(template)

# Load the Mistral model
model = OllamaLLM(model="mistral")

# Ask a question
chain = prompt | model
response = chain.invoke({"question": "What is MoE in AI?"})

print(response)`

When you run this, the model will provide an answer. For example, if you ask *"What is MoE in AI?"*, it will give an explanation about Mixture of Experts (MoE), a neural network architecture.
