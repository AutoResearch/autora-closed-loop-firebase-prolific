# AutoRA Workflow

The researcher_hub contains a basic template for an AutoRA workflow with sweetBean.

To install the necessary dependencies, move to the directory to the and install the requirements.

Move to the researcher_hub directory
```shell
cd researcher_hub
```

```shell
pip install -r requirements.txt
```

## Add credentials

The autora-firebase-runner will need access to your firebase project. Therefore, we need credentials. You find them here:
(https://console.firebase.google.com/)
  -> project -> project settings -> service accounts -> generate new private key

Copy them into the firebase_credentials in the file `autora_workflow.py` in the `research_hub`-folder.
