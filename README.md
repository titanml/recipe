# Recipe
## Quick Start on Launching Takeoff with Dedicated Recipes

### Prerequisites:
- **Install Docker**
- **Install NVIDIA Container Toolkit for GPU models**
- **Access to Takeoff**:
  - Run `docker login -u takeoffusers` and paste the Docker authentication token
  - Alternatively, use `docker run` with `-e LICENSE_KEY=[your_license_key]`
- **Download a Source Code Editor** like Visual Studio Code

### Step 1: Fork and Clone the Recipe Repository
- Fork and clone the [Recipe repository](https://github.com/titanml/recipe.git)

### Step 2: Gain Access to Models
- Sign agreements and submit details for popular models, else you can ignore this part (e.g., meta-llama/Meta-Llama-3.1-8B-Instruct)
- Explore models that do not require user information, like those on [Hugging Face](https://huggingface.co/)

### Step 3: Set Your License Key, Hugging Face Token, and Task

You can either export the license key, Hugging Face token, and task directly in your terminal or use a `.env` file.

#### Option 1: Export in Terminal
- For Linux/macOS:
    ```bash
    export LICENSE_KEY="your_license_key"
    export TAKEOFF_ACCESS_TOKEN="your_hf_token"
    export TASK="your_task" # e.g., text_generation, chatbot, summarization
    ```
- For Windows (Command Prompt):
    ```cmd
    set LICENSE_KEY=your_license_key
    set TAKEOFF_ACCESS_TOKEN=your_hf_token
    set TASK=your_task # e.g., text_generation, chatbot, summarization
    ```
- For Windows (PowerShell):
    ```powershell
    $env:LICENSE_KEY="your_license_key"
    $env:TAKEOFF_ACCESS_TOKEN="your_hf_token"
    $env:TASK="your_task" # e.g., text_generation, chatbot, summarization
    ```

#### Option 2: Use a `.env` File
- Create a `.env` file in the root directory of the cloned repository and add your keys:
    ```bash 
    LICENSE_KEY=your_license_key
    TAKEOFF_ACCESS_TOKEN=your_hf_token
    TASK=your_task # e.g., text_generation, chatbot, summarization
    ```
- Ensure that your configuration file (e.g., `config.yaml`) references these variables:
    ```bash 
    license_key: '${LICENSE_KEY}'
    takeoff_access_token: '${TAKEOFF_ACCESS_TOKEN}'
    task: '${TASK}'
    ```

### Step 4: Configure `config.yaml` (Recipes)
- Edit `config.yaml` with:
  - `model_name`: Set the model you want to use for the selected task
  - `device`: cuda/cpu
  - `consumer_group`: generate/embed/reranker
  - `license_key`: should be set as an environment variable or in the `.env` file
  - `takeoff_access_token`: should be set as an environment variable or in the `.env` file
  - `task`: should be set as an environment variable or in the `.env` file

### Step 5: Launch Takeoff
- Navigate to the cloned repository:
  - `cd <directory_name>/recipe`
- Run `docker compose up` in your terminal



### Task-Specific Configuration

These folders contain specific yaml files for different use cases:

| Tasks                     | Description                        | Use Cases                         |
|---------------------------|------------------------------------|-----------------------------------|
| Text Generation           | Text generation for creative writing | Content creation, storytelling    |
| Chatbot                   | Interactive conversation simulation | Customer support, virtual assistants |
| Summarization             | Condensing lengthy text             | Research analysis, report generation |
| Question Answering        | Providing answers to queries        | Information retrieval, educational support |
| Code Generation           | Writing code based on input         | Software development, automation  |
| Image-Text-to-Text        | Describing images with text         | Image captioning, accessibility features |
| Visual Question Answering | Answering questions based on images | E-learning, visual analysis       |

### Optional: Troubleshooting
- **Docker errors**: Ensure Docker is running properly and you have sufficient permissions.
- **Environment variables not detected**: Verify that the environment variables are set correctly. Use `echo $VARIABLE_NAME` to check.
- **Model loading issues**: Check if the model name is correct in the `config.yaml` and the model is accessible.

