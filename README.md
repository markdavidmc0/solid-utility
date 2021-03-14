# solid-utility
Python wrapper for interaction with a SOLID pod.

## Contents
[Introduction](##Introduction) </br>
[Self Hosted Pod](##Self  Hosted  Pod) </br>
[Prerequisites](##Prerequisites) </br>
[Build the Application](##Build  The  Application) </br>
[Run the Application](##Run  The  Application) </br>
[Additional Information](##Additional  Information) </br>

## Introduction
A SOLID pod is the first grand idea since the creation of the WWW (World Wide Web) that offers a solution to data protection and privacy online.

Currently, a SOLID pod (individual secure online space) is created using the npm package manager for Node.js. This projects aims to create similar support for Python.

## Self Hosted Pod

The implementation of the Python SOLID Utility assumes a self-hosted pod for maximum control and security. AWS, Azure, Google Cloud and IBM Cloud are supported for hosting.

## Prerequisites
1) [Register your pod and create your profile](https://solidproject.org/developers/tutorials/getting-started#prerequisites)
2) [Install pip](https://pip.pypa.io/en/stable/installing/)
3) [Install FastAPI](https://fastapi.tiangolo.com/tutorial/)

## Build the Application
<details>
<summary>Initialise the application.</summary>

1) Create a directory for the application:  
    ```
    mkdir my-demo-app
    ```
2) Enter into the newly created directory:  
    ```
    cd my-demo-app
    ```
3) Create a brand new application:
    ```
    pip install solid-utility
    ```
</details>

<details>
<summary>Create the application.</summary>

In the `my-demo-app` directory, create the files for the application.

1) Create a `my-demo.css` file with the following content:

    ```css
    h2,
    h3 {
        margin: 1rem 1.2rem 1rem 1.4rem;
    }

    header {
        border-bottom: #5795b9 solid;
        padding-left: 0.5rem;
    }

    .panel {
        border: 1px solid #005b81;
        border-radius: 4px;
        box-shadow: rgb(184, 196, 194) 0px 4px 10px -4px;
        box-sizing: border-box;

        padding: 1rem 1.5rem;
        margin: 1rem 1.2rem 1rem 1.2rem;
    }

    #login {
        background: white;
    }

    #read {
        background: #e6f4f9;
    }

    .labelStatus[role="alert"] {
        padding-left: 1rem;
        color: purple;
    }

    .display {
        margin-left: 1rem;
        color: gray;
    }

    dl {
        display: grid;
        grid-template-columns: max-content auto;
    }

    dd {
        font-weight: bold;
    }
    ```

2) Create an `index.html` file with the following content:

    ```html
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="utf-8" />
            <title>Getting Started: Python Client Libraries</title>
            <script defer src="./index.js"></script>
            <link rel="stylesheet" href="my-demo.css" />
        </head>

        <body>
            <header>
                <h2>Getting Started</h2>
                <h3>with Python Client Libraries</h3>
            </header>
            <section id="login" class="panel">
                <div class="row">
                    <label id="labelLogin" for="btnLogin"
                        >1. Click the button to log into
                        <span id="solid_identity_provider"
                            >...provided by the Python code...</span
                        >:
                    </label>
                    <button name="btnLogin" id="btnLogin">Login</button>
                    <p id="labelStatus" class="labelStatus"></p>
                 </div>
            </section>

            <div id="read" class="panel">
                <div class="row">
                    <form id="writeForm">
                        <label id="writelabel" for="name">2. Write your     name: </label>
                        <input
                            type="text"
                            id="input_name"
                            name="name"
                            size="50"
                            placeholder="Your name here"
                        />
                        <button type="submit">
                            Write to Profile
                        </button>
                    </form>
                </div>

                 <dl class="display">
                    <dt>Writing status:&nbsp</dt>
                    <dd id="labelWriteStatus" class="labelStatus">...not written yet...</dd>
                </dl>
            </div>

            <div id="read" class="panel">
                <div class="row">
                    <form id="readForm">
                        <label id="readlabel" for="webID"
                        >3. Read back name (anyone's!) from their WebID:
                        </label>
                        <input
                            type="url"
                            id="webID"
                            name="webID"
                            size="50"
                            placeholder="...not logged in yet - but enter any WebID to read from its profile..."
                        />
                        <button type="submit" name="btnRead" id="btnRead">
                            Read Profile
                        </button>
                    </form>
                </div>
                <dl class="display">
                    <dt>Formatted Name (FN) read from Pod:&nbsp</dt>
                    <dd id="labelFN">...not read yet...</dd>
                </dl>
            </div>
         </body>
    </html>
    ```

</details>

## Run the Application
1) In the `my-demo-app directory`, run:
    ```
    unicorn main:app --reload
    ```
    The output should resemble the following:
    ```
    INFO: Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
    ```
2) Open `http://127.0.0.1:8000` in a browser.

3) Click the Login button.
    - The first time you log into your Pod with this application (it’ll be named `http://127.0.0.1:8000`), you’ll be prompted to authorize it to access your Pod . To allow the application to read and write to your Pod, click `Authorize`.
    - If you have logged out of your Pod, you are prompted to log in. Enter your username and password to log in.
    - Once logged in, you should be redirected back to the client application.

    Back in the application, you should see a message stating `Your session is logged in with the WebID [<your WebID>]`. and the WebID textfield should display your WebID.

4) Now that you’re logged in, you can read and write the information in your Solid profile.

    1) First, click the `Read Profile` button.
        You should see the name you entered when you registered your Pod.

    2) To update your name, enter a new name in the `2. Write your name` textfield, and click the Write to Profile button. You should see the message:
        ```
        Wrote [<your new name>] as name successfully!
        ```
    3) Verify that your profile was updated by clicking on the `Read Profile` button again. You should see the updated name displayed!

    You can also read the public profiles of anyone else in the world with a Solid Pod. Enter the WebID of the person whose profile you wish to read; e.g., `https://docs-example.inrupt.net/profile/card#me`.

5) Exit the Application. To exit the application, stop the `npx parcel` process; e.g., `Ctrl-C`.

## Additional Information
### API Documentation
[API docs](https://solidproject.org/developers/tutorials/getting-started#additional-information)

### Parameters
    WebID - unique ID for SOLID pod.
