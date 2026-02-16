# Intelligent Monitoring (Agentic AI) Spike

This repository contains an experimental spike investigating how agentic AI could be employed to automate the monitoring of real-time / live data feeds to pick out relevant data for decision-making. The specific use case we are exploring is monitoring news feeds for relevant articles related to the UK public sector.

## Prequisites

- [Python](https://docs.python.org/3/using/index.html) `>= 3.13.7` - We recommend using [uv](https://docs.astral.sh/uv/getting-started/installation/) to manage your Python environment.
- [pipx](https://pipxproject.github.io/pipx/installation/)
- [uv](https://docs.astral.sh/uv/getting-started/installation/)
- [Azure AI Foundry](https://azure.microsoft.com/en-gb/products/ai-foundry/) - With GPT5 Nano access for the LLM experiments.
- [Docker](https://docs.docker.com/get-docker/) - Optional if you want to run the OpenTelemetry Collector for tracing.

## Setup

### Python Environment

Please install python `>= 3.13.7` and `pipx` in your environment. This project uses [uv](https://github.com/astral-sh/uv) to manage the environment and dependencies.

```python
# install uv via pipx
pipx install uv

# sync dependencies
uv sync

# create jupyter kernel
uv run task create-kernel
```

### VS Code Setup
If you are running the notebooks in VS Code, we recommend installing the following extensions:
- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) - For Python language support.
- [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter) - For Jupyter notebook support.

Ensure that the Jupyter kernel created by `uv` is selected in your VS Code environment which should be named `ai-agent-swarm-spike`.

### Jupyter Server
If you prefer to run a Jupyter server directly, you can do so with the following command:

```bash
uv run --with jupyter jupyter lab
```

### Environment Variables

This project uses a `.env` file stored in the `./notebooks` directory to manage environment variables. An example `.env.example` file is provided. Please copy this file to `./notebooks/.env` and fill in the required values.

```bash
cp notebooks/.env.example notebooks/.env
```

Below is a description of the environment variables:

| Variable                    | Required | Default               | Description                                      |
|-----------------------------|----------|-----------------------|--------------------------------------------------|
| `AZURE_OPENAI_ENDPOINT`     | Yes      | None                  | Azure OpenAI service endpoint URL               |
| `AZURE_OPENAI_API_KEY`      | Yes      | None                  | API key for accessing Azure OpenAI service      |
| `OPENAI_API_VERSION`        | Yes      | `2024-05-01-preview`  | Azure OpenAI API version                        |

`AZURE_OPENAI_ENDPOINT` may point to an Azure AI Foundry project/resource (this is the preferred and tested option for the experiments in this repository), or it can point directly to an Azure OpenAI Service endpoint. We recommend using an AI Foundry resource where possible — if you choose to use Azure OpenAI Service directly, ensure the endpoint URL and `AZURE_OPENAI_API_KEY` correspond to that service.

## Notebooks
The experiments are contained within Jupyter notebooks located in the `notebooks/` directory.

Further documentation is provided within each notebook and in the [Experiment Writeup](experiment-writeup.md).
