# Welcome

This repository contain the instructions for the workshop "Deep-learning 
retoration for microscopy images", held at Pasteur Institute (Paris) on 
the 31.05.23.

## How to run this site locally

1. Clone this repository

    ```bash
    git clone https://github.com/nobias-fht/advanced-scripting.git
    ```

2. In a conda env, install the relevant packages:

    ```bash
    pip install -r requirements.txt
    ```

3. Install the commit pre-hooks

    ```bash
    pip install pre-commit
    pre-commit install
    ```

4. Then generate the site:

    ```bash
    mkdocs serve
    ```
