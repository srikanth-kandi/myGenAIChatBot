# ChatBot with OpenAI and LangChain

[Main Handbook](https://inky-ironclad-8d2.notion.site/Generative-AI-Workshop-bfb0123ccf6945ebbfa5bf3328917423), [This handbook](https://inky-ironclad-8d2.notion.site/ChatBot-with-Open-AI-and-LangChain-Handbook-36aee0b81838457e91a14c4ddf3378ce)

<!----Prerequisites---->

<details>
<summary><b>Prerequisites</b></summary>

- **Existing Open AI Account:**

    - Check whether you have a limit to using the Open AI API

    - The below screenshot indicated it is expired by June 1. So, you need to create a new account.

        ![Free trail expired](./images/free-usage-expired-open-ai-api.png)

    - Check your API key usage <a href="https://platform.openai.com/account/usage" target="_blank">here</a>

- **Creating Open AI Account with New Mail and New Phone Number:**

    - Open <a href="https://openai.com/" target="_blank">https://openai.com</a>

    - Click on `Sign Up` button

    - Choose your preffered Sign Up method

    - After logged in click <a href="https://platform.openai.com/apps" target="_blank">here</a> to see below options

        ![OpenAI Options](./images/openai-options.png)

- **Create a Hugging Face Account**
    
    - Open [https://huggingface.co/](https://huggingface.co/)

    - Click on `Sign Up` button

    - Enter your details and Click on `Sign Up` button

    - Verify your email address

- **Create a New Space in Hugging Face Account**
    
    - Click on Profile icon top right

        ![Hugging face profile icon](./images/hugging-face-profile-icon.png)
    
    - Click on `New Space`

        ![Hugging face new space](./images/hugging-face-new-space.png)

    - Enter below details of your new space

        ![Hugging face new space details](./images/hugging-face-new-space-details.png)

- **Open the below provided Colab link**

    <a href="https://colab.research.google.com/drive/1miK4Xbqv9lYkfe0z6jMh41fA_itulAA0?usp=sharing" target="_blank"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>


- **Copying Code to your Google Drive**

    - On the top left corner of Google Colab Notebook you can find `File`, click on it

        ![Google Colab File Section](./images/google-colab-file-section.png)

    - Click on `Save a copy in Drive`

        ![Google Colab Save a copy in Drive](./images/google-colab-save-a-copy-in-drive.png)
    
    - If you are not logged in to your Google Account, please log into it.

    - Once you are successfully logged in a new Google Colab Notebook with the given code will be opened
</details>

<!------Install the required packages-------->

<details>
<summary><b>Install the required packages</b></summary>

- Click on the Play button to Install the Packages

    ![Google Colab pip install section](./images/google-colab-pip-install-section.png)
</details>

<!-----Importing the required packages------->

<details>
<summary><b>Importing the required packages</b></summary>

- Click on the Play button to import the required things to build the application

    ![Google Colab import section](./images/google-colab-import-section.png)
</details>

<!----Get the OpenAI API Key and Set as ENV variable---->

<details>
<summary><b>Get the OpenAI API Key and set it as environmental variable</b></summary>

- Generate API Key

    -  Go to <a href="https://platform.openai.com/account/api-keys" target="_blank">https://platform.openai.com/account/api-keys</a>

    - Click on `+ Create new secret key`

    - Copy the Secret Key for your use

- Replace your `OPENAI_API_KEY` with your own API Key

    ![Google Colab OpenAI API Key](./images/google-colab-openai-api-key.png)

- Click on the Play button

    ![Google Colab OpenAI API Key Play Button](./images/google-colab-openai-api-key-play.png)
</details>

<!----Assigning the values for template, prompt, and memory---->

<details>
<summary><b>Assigning the values for template, prompt, and memory</b></summary>

- You can update the first line of the template with <a href="./prompts-and-examples.md" target="_blank">Prompts and Examples</a> provided

- Click on the Play button

    ![Google Colab template section](./images/google-colab-template-section.png)
</details>

<!----Initializing LLM Chain using OpenAI---->

<details>
<summary><b>Initializing LLM Chain using OpenAI</b></summary>

- Using `ChatOpenAI` method we are creating an <a href="https://js.langchain.com/docs/api/chains/classes/LLMChain" target="_blank">LLM Chain</a>

- Click on the Play button

    ![Google Colab LLM Chain section](./images/google-colab-llm-chain-section.png)
</details>

<!-----Defining a function to generate the response for the question you ask---->

<details>
<summary><b>Define a function to generate the response for the question you ask</b></summary>

- From the initialized `llm_chain` we will predict the response

- Click on the Play button

    ![Google Colab LLM Chain Response](./images/google-colab-llm-chain-response.png)
</details>

<!-----Creating a Chat Interface using Gradio------->

<details>
<summary><b>Create a Chat Interface using Gradio</b></summary>

- We are creating the `ChatInterface` from gradio and providing a function `get_text_response` and also examples from <a href="./prompts-and-examples.md" target="_blank">Prompts and Examples</a> provided

- Check for other arguments <a href="https://www.gradio.app/docs/chatinterface" target="_blank">here</a>

- Click on the Play button to create an interface

    ![Google Colab Gradio Chat Interface](./images/google-colab-gradio-chat-interface.png)
</details>

<!-----Launch your ChatBot with Gradio App------>

<details>
<summary><b>Launch your ChatBot with Gradio App</b></summary>

- Click on the Play button to launch the App

    ![Google Colab Gradio Chat Interface Launch](./images/google-colab-gradio-chat-interface-launch.png)
</details>

### Now you can try asking questions in your ChatBot

<!----If you are getting any errors---->

<details>
<summary><b>If you are getting any errors</b></summary>

-  Keep print statements to identify the issue

- To identify the error you are getting please add `debug = True` while launching the gradio app

    ```python
    if __name__ == "__main__":
        demo.launch(debug = True)
    ```

    ```python
    def get_text_response(user_message,history):
        try:
            response = llm_chain.predict(user_message = user_message)
        except Exception as e:
            print("Error:", e)
            try:
                print("Error:", e.error.message)
                response = "Failed to reply: " + e.error.message
            except Exception as e:
                response = "Failed to reply"
        return response
    ```
</details>

### Publish your code to Hugging Face

<details>
<summary><b>Login to Hugging Face from Google Colab</b></summary>

- Create a Hugging Face token and Copy

    - Login to Hugging Face <a href="https://huggingface.co/" target="_blank">https://huggingface.co/</a>

    - Open <a href="https://huggingface.co/settings/tokens" target="_blank">https://huggingface.co/settings/tokens</a>

    - Click on `New token`

    - Add a Name for the Token

    - Choose `write` Role for the Token

    - Click on `Generate a token`

    - Copy the Token

    - Click on Play button to enter Hugging Face Token

        ![Google Colab Hugging Face Token](./images/google-colab-hugging-face-token.png)

    - Now paste the Hugging Face token in the textbox provided and click on `Login`

        ![Google Colab Hugging Face Token Login](./images/google-colab-hugging-face-token-login.png)
</details>

<!-----Create Hugging Face API to push code from Google Colab------>

<details>
<summary><b>Create Hugging Face API to push code from Google Colab</b></summary>

- Click on the Play button to create API

    ![Google Colab Hugging Face API](./images/google-colab-hugging-face-api.png)
</details>

<!----Adding Hugging Face Repository ID----->

<details>
<summary><b>Adding Hugging Face Repository ID</b></summary>

- Copy Hugging Face Repository ID by opening the Hugging Face Repo Created

    ![Hugging Face Repo ID](./images/hugging-face-repo-id.png)

- Replace your Repo ID

    ![Replace Hugging Face Repo ID](./images/replace-hugging-face-repo-id.png)

- Click on Play button to assign Hugging Face Repo ID

    ![Replace Hugging Face Repo ID Play Button](./images/replace-hugging-face-repo-id-play.png)
</details>

<!-----Adding OpenAI API Key to Hugging Face----->

<details>
<summary><b>Add OPENAI_API_KEY in Hugging Face Repository secrets</b></summary>

- Click on Settings Button

    ![Hugging Face Settings Button](./images/hugging-face-settings-button.png)

- Go to `Variables and secrets` section

    ![Hugging Face Variables and secrets section](./images/hugging-face-variables-and-secrets-section.png)

- Click on `New secret`

    ![Hugging Face New secret](./images/hugging-face-new-secret.png)

- Enter Name as `OPENAI_API_KEY` and Value as your OpenAI API Key

    ![Hugging Face Name and Value](./images/hugging-face-name-and-value.png)
</details>

<!-----Load Application Files and Requirements file----->

<details>
<summary><b>Load Application and Requirement files</b></summary>

- Click on the Play button to download files

    ![Google Colab Download Files](./images/google-colab-download-files.png)

- You can see downloaded files here

    ![Google Colab Downloaded Files](./images/google-colab-downloaded-files.png)
</details>

<!-----Editing the downloaded files------>

<details>
<summary><b>Editing the Application file</b></summary>

- Click on the `app.py` file

    ![Google Colab Edit app.py](./images/google-colab-edit-app-py.png)

- The file will be opened and you can edit the `<Prompt>` and `<Example>` as per <a href="./prompts-and-examples.md">Prompts and Examples</a> and save using `⌃ + S` or `⌘ + S`

    ![Google Colab Modify app.py](./images/google-colab-modify-app-py.png)
</details>

<!-------Push your code to Hugging Face-------->

<details>
<summary><b>Push your code to Hugging Face</b></summary>

- Click on Play button

    ![Google Colab api upload_file](./images/hugging-face-push-code.png)

- Now in your space, you should see it is `Building`

    ![Hugging Face Building](./images/hugging-face-building.png)

- On Succesful build, you should see `Running`

    ![Hugging Face Running](./images/hugging-face-running.png)

- If the Building fails, you will see a `Runtime error` with some errors below

    ![Hugging Face Runtime Error](./images/hugging-face-runtime-error.png)

- Click on Logs to check more details about the `error`
</details>

---

<h3 align = 'center'>Show some ❤️ by starring ⭐ this repository!</h3>
