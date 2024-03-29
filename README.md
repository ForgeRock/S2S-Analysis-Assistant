# Overview

Automate analysis of collected configurations from Self-managed deployment for AM, IDM, IG and DS

* "Fit for Purpose" for ID Cloud
* "High-level" effort analysis



# Setup and configuration

The purpose of this guide is to help users start and run the S2S Analysis Assistant and, if needed, setup the environment for further development of the application.
The docker compose stack will reuse the same docker Platform UI image of the S2S tool and, it will use the rock-beats for the backend:
* analysis-assistant-ui (the main console of the tool);
* analysis-assistant-server (backend)



## Run the full docker stack
**1. Prerequisites:**

- docker => 20.10
- docker-compose => 2.0.0
- gcloud


**1.1. Instalation of docker locally:**

1.1.1 docker-desktop available for Mac, Linux and Windows operating systems

> Can be downloaded and installed from [here](https://www.docker.com/products/docker-desktop).


1.1.2 docker-compose

> If you have already installed Docker Desktop then there is no need of separate installation for docker compose, since its part of the package.

> [Install docker-compose](https://docs.docker.com/compose/install/)


**2. Clone the repo**

```
git clone https://github.com/ForgeRock/S2S-Analysis-Assistant.git
```


**3. Install (if case) and authenticate to the Google Cloud, to access the private docker images repo**

- Install gcloud https://cloud.google.com/sdk/docs/install

- Execute `gcloud auth configure-docker` from terminal


**4. Run the complete docker stack locally:**

`cd docker-analysis-assistant`

> Edit **env_custom** file and change all the endpoints accordingly if needed:
* _**APP_NAME**_ should be: DATA_ANALYSE_TOOL
* _**EXT_SERVER_HTTP**_ should be the PORT where the S2S ANALYSIS ASSISTANT BACKEND instance is running
* port for the S2S ANALYSIS ASSISTANT Platform Console in _**EXT_UI_HTTP**_
* port for the S2S ANALYSIS ASSISTANT BACKEND in _**EXT_SERVER_HTTP**_
* if the previous port was changed then it should be updated also in the **_VUE_APP_IDM_URL_**

Before starting the application you have to check that you have proper rights to access and download the docker images from the Forgerock container repository.

Bring up the stack:

`docker-compose --env-file env_custom up -d`


> Check if the S2S tool has successfully started:

* S2S Analysis Assistant Admin UI - http://localhost:8082 (no authentication will be needed)


**5. Run the complete docker stack locally with an updated docker image:**

`cd docker-analysis-assistant`

`docker-compose --env-file env_custom pull && docker-compose --env-file env_custom stop && docker-compose --env-file env_custom up -d`
