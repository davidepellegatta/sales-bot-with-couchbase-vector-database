## Overview

In this notebook you'll take an Amazon product reviews dataset from Kaggle and use OpenAI gpt-4o to obtain product review summaries, upsert those summaries in a vector database, then use Retrieval Augmented Generation (RAG) to power a sales chatbot that can make targeted product recommendations.

Let's take a look at the overall workflow:
1. We start with a dataset that contains over 10,000 reviews across 900 Amazon musical instruments and accessories.
2. Using gpt-4o chat, we generate summaries of product reviews for each product from the 20 most recent reviews. We format the summaries in JSON format.
3. We then take the summaries and upsert them into a vector database (Couchbase in this case)
4. We then use Couchbase vector Indexes and gpt-4o instruct to build a RAG-based sales chatbot that provides targeted recommendations to the user based on the products that are present in the inventory.

### OpenAI
We'll use [OpenAI](https://platform.openai.com/) to power all of the GenAI model needs of this notebook: LLMs, image gen, image animation.
* To use OpenAI model, you'll need to go to https://platform.openai.com/ and sign in .
* Next you'll need to generate an API token by following these [instructions](https://platform.openai.com/docs/quickstart). Keep the API token in hand, we'll need it further down in this notebook.

In this example we will use the gpt-4o instruct model.


### Couchbase
We'll use Couchbase Capella for our vector database. You can create your [free account here](https://cloud.couchbase.com/sign-up) with your GitHub account or your email.


### Local Python Notebook

Open your terminal or command prompt and use the `cd` command to navigate to the directory where your Jupyter notebook is located. For example:

```bash
cd /path/to/your/sales-bot-with-couchbase-vector-database
```

Use the `venv` module (or `virtualenv` if you prefer) to create a new virtual environment within that directory:

```bash
python -m venv .venv  # Creates a virtual environment named '.venv'
```

Activate the environment to start using it:

```bash
source .venv/bin/activate  # On Linux/macOS
.venv\Scripts\activate  # On Windows
```

This allows Jupyter to recognize your virtual environment:

```bash
pip install ipykernel
```

This makes your virtual environment selectable within Jupyter:

```bash
python -m ipykernel install --user --name=.venv --display-name="My Notebook Env"
```
(Replace "My Notebook Env" with a descriptive name for your kernel.)

* **Start Jupyter Notebook:**  `jupyter notebook`
* **Open SalesBot_Couchbase.ipynb**
* **Select the kernel:** Go to "Kernel" -> "Change kernel" and choose the kernel you just created ("My Notebook Env").

You don't need to install additional pip packages ahead of running the notebook, since those will be installed right at the beginning. You will need to ensure your system has `imagemagick` installed by following the [instructions](https://imagemagick.org/script/download.php).

## Remember if you already have your virtul environment, remember just to source it again:

```bash
source .venv/bin/activate
```
