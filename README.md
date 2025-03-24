# Azure OpenAI Example with Splunk

## Prerequisites

* Azure account with Azure OpenAI enabled (refer to this [document](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/create-resource?pivots=web-portal) for details)
* Azure OpenAI deployment with gpt-35-turbo model 
* Splunk distribution of OpenTelemetry collector running on the host where the example is deployed

## Steps to run the example

``` bash
# clone the repo if you haven't already
git clone https://github.com/dmitchsplunk/azure-openai-example.git

# navigate to the directory repo
cd azure-openai-example

# create a virtual environment 
python3 -m venv openai-env

# activate the virtual environment
source openai-env/bin/activate

pip install openai==1.68.2

export AZURE_OPENAI_API_KEY="REPLACE_WITH_YOUR_KEY_VALUE_HERE"
export AZURE_OPENAI_ENDPOINT="REPLACE_WITH_YOUR_ENDPOINT_HERE"

python app.py
```

## Add the Splunk Distribution of OpenTelemetry Python

``` bash
export OTEL_SERVICE_NAME=azure-openai-example
export OTEL_RESOURCE_ATTRIBUTES='deployment.environment=test'
export PYO3_USE_ABI3_FORWARD_COMPATIBILITY=1
export OTEL_EXPORTER_OTLP_ENDPOINT=http://localhost:4317
export OTEL_EXPORTER_OTLP_PROTOCOL=grpc

pip install splunk-opentelemetry==1.21.0

./openai-env/bin/splunk-py-trace-bootstrap        

pip3 install openlit==1.33.4 opentelemetry-api==1.27.0

./openai-env/bin/splunk-py-trace python app.py 
```

You should see traces in Splunk Observability Cloud that look like the following: 

![Example trace](./images/trace.png)