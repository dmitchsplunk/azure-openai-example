# Azure OpenAI Example with Splunk

``` bash
# clone the repo if you haven't already
git clone https://github.com/dmitchsplunk/azure-openai-example.git

# navigate to the directory repo
cd azure-openai-example

# create a virtual environment 
python3 -m venv openai-env

# activate the virtual environment
source openai-env/bin/activate

pip install openai

export AZURE_OPENAI_API_KEY="REPLACE_WITH_YOUR_KEY_VALUE_HERE"
export AZURE_OPENAI_ENDPOINT="REPLACE_WITH_YOUR_ENDPOINT_HERE"

python app.py
```

