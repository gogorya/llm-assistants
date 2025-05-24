# LLM Assistants

Simple Docker Compose files for a quick local (or VM) setup of LLMs with NVIDIA GPUs.

## Getting Started

### Prerequisites

- [Install Docker](https://docs.docker.com/get-docker)
- [Install NVIDIA Drivers](https://www.nvidia.com/en-us/drivers/)
- [Install NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#setting-up-nvidia-container-toolkit)

### Documentations

- [open-webui](https://docs.openwebui.com)
- [ollama](https://github.com/ollama/ollama/blob/main/docs/docker.md)
- llama.cpp
  - [server](https://github.com/ggml-org/llama.cpp/blob/master/tools/server/README.md)
  - [docker](https://github.com/ggml-org/llama.cpp/blob/master/docs/docker.md)
- [tabby](https://tabby.tabbyml.com/docs/welcome)

## Usage

1.  Clone this repository:

    ```sh
    git clone git@github.com:gogorya/llm-assistants.git
    ```

2.  Make local directories (optional):

    ```sh
    cd llm-assistants/
    mkdir -p llama.cpp/models/ ollama/ open-webui/ tabby/
    ```

3.  Using Docker Compose Files:

    - Chat assistant (open-webui: [http://localhost:8080](http://localhost:8080)):

      ```sh
      # start
      docker compose -f docker-compose.chat.yaml up -d
      # stop
      docker compose -f docker-compose.chat.yaml down
      ```

    - Code assistant (tabby: [http://localhost:8080](http://localhost:8080)):

      ```sh
      # start
      docker compose -f docker-compose.code.yaml up -d
      # stop
      docker compose -f docker-compose.code.yaml down
      ```

4.  For llama.cpp setup:
    - Download models (from [Hugging Face](https://huggingface.co/models?sort=trending&search=gguf)) and store in `/llama.cpp/models/`.
    - Uncomment `llamacpp-server` service inside `docker-compose.chat.yaml` and add model in `LLAMA_ARG_MODEL` environment variable.

## Notes

- The Docker Compose files are not supposed to run altogether.
- Check environment variables.
- Recommended to run either ollama or llamacpp-server.
- Refer to the mentioned documentations for configuration and setup.

## Acknowledgements

- [open-webui](https://github.com/open-webui/open-webui)
- [ollama](https://github.com/ollama/ollama)
- [llama.cpp](https://github.com/ggml-org/llama.cpp)
- [tabby](https://github.com/TabbyML/tabby)
