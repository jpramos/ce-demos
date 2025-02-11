# test_langchain_template

## Installation

Install the LangChain CLI if you haven't yet

```bash
pip install -U langchain-cli
```

## Adding packages

```bash
# adding packages from 
# https://github.com/langchain-ai/langchain/tree/master/templates
langchain app add $PROJECT_NAME

# adding custom GitHub repo packages
langchain app add --repo $OWNER/$REPO
# or with whole git string (supports other git providers):
# langchain app add git+https://github.com/hwchase17/chain-of-verification

# with a custom api mount point (defaults to `/{package_name}`)
langchain app add $PROJECT_NAME --api_path=/my/custom/path/rag
```

Note: you remove packages by their api path

```bash
langchain app remove my/custom/path/rag
```

## Setup LangSmith (Optional)
LangSmith will help us trace, monitor and debug LangChain applications. 
LangSmith is currently in private beta, you can sign up [here](https://smith.langchain.com/). 
If you don't have access, you can skip this section


```shell
export LANGCHAIN_TRACING_V2=true
export LANGCHAIN_API_KEY=<your-api-key>
export LANGCHAIN_PROJECT=<your-project>  # if not specified, defaults to "default"
```

## Launch LangServe

```bash
langchain serve --port 8080
```

## Private Cloud Runs

To see the private websites such as qna/docs you need to see it locally via the gcloud proxy>

```sh
gcloud run services proxy langserve --region=europe-west1
```

Can then view at `http://localhost:8080/docs`

### Multivac URL

```bash
curl http://localhost:8080/pirate_speak/invoke \
  -H "Content-Type: application/json" \
  -d '{
    "input": {"question":"Who is Mark Edmondson?"}
  }'

```
