# Ollama 

Ollama facilitates running local LLMs on your computer. 

## Getting started 

* [Ollama](https://ollama.com/)
  * Options for interacting with Ollama
    * CLI - Terminal, iTerm, ...
    * API - `curl`, Postman, ...
    * User interface - Open WebUI, LMStudio, ...
  * [GitHub](https://github.com/ollama/ollama)
  * [Docs](https://github.com/ollama/ollama/tree/main/docs)
  * [Models](https://ollama.com/search)
    * Qwen 2.5-Coder is an example of a [code specific model](https://ollama.com/library/qwen2.5-coder:32b).
  * Localhost: `http://localhost:11434/`
  * `ollama pull llama3.2`
  * `ollama run llama3.2`
  * `ollama rm llama3.2`
  * `ollama list`
  * `/bye`
* Sample [API](https://github.com/ollama/ollama/blob/main/docs/api.md) usage

  ```
  curl http://localhost:11434/api/generate -d '{
      "model": "phi4",
      "prompt":"When were you trained",
      "stream": false
  }' 
  ```
* [Open WebUI](https://docs.openwebui.com)
    * Installing Open WebUI
      * [Docs](https://docs.openwebui.com/)
      * Install `uv` 
        * `curl -LsSf https://astral.sh/uv/install.sh | sh`
      * Install Open WebUI
        * `DATA_DIR=~/.open-webui uvx --python 3.11 open-webui@latest serve`
      * Run Open WebUI on localhost
        * Runs on localhost `http://localhost:8080/`
* Modelfile
  * An example of a `Modelfile`

    ```
    FROM llama3.2

    # sets the temperature to 1 [higher is more creative, lower is more coherent]
    PARAMETER temperature 1

    # sets the context window size to 4096, this controls how many tokens the LLM can use as 
    context to generate the next token
    PARAMETER num_ctx 4096

    # sets a custom system message to specify the behavior of the chat assistant
    SYSTEM You are Mario from super mario bros, acting as an assistant.
    ```
  * To use the `Modelfile` you created follow these steps:
    * Save your file without extensions, e.g. `Modelfile`
    * `ollama create <choose your model name, e.g. mario> -f <location of the file e.g. ./Modelfile>`
    * `ollama run <choose your model name>`
    * Start using the model

***

## Terminology 

* LLM - Large language model
  * Model
   * Architecture
     * e.g. LLama
   * Parameters
     * e.g. 14B
  * Context length
  * Embedding length
  * Quantization
* Embeddings
* Token
* Distillation (distill): knowledge from a larger, more complex model (often referred to as the "teacher") to a smaller,simpler model (the "student")
* Text generation 
  * Phi4
* Code generation
  * Qwen 2.5-Coder
* Multimodal applications
  * Llava

***

## Resources 

* [Ollama](https://ollama.com)
* [FAQ](https://github.com/ollama/ollama/blob/main/docs/faq.md)
* [Ollama API](https://github.com/ollama/ollama/blob/main/docs/api.md)
