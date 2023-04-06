**Instructions to run the S2S Analyse Tool using Forgerock Public Docker Registry**

**1. Clone the repo**

```
git clone https://github.com/ForgeRock/Software-to-SAAS-Accelerators.git
git checkout develop
```

**2. Install (if case) and authenticate to the Google Cloud, to access the private docker images repo**

- Install gcloud https://cloud.google.com/sdk/docs/install

- Execute `gcloud auth configure-docker` from terminal


**3. Run locally the complete S2S docker stack:**

`cd docker-analysis-assistant`

- Bring up the stack:

`docker-compose --env-file env_custom up -d`

- Important note: the same docker image and env_custom configuration file can be used for the Software-to-SAAS-Accelerators and S2S Data Analysis tool with the following flags:
	+ APP_NAME possible values: S2S or DATA_ANALYSE_TOOL
	+ EXT_SERVER_HTTP should be the PORT where the S2S ROCKBEATS BACKEND instance is running

- Access the endpoints:

=> S2S Analysys Assistant Platform UI: http://localhost:8082

**4. Run the complete docker stack locally with an updated docker image:**

`cd docker`
`docker-compose --env-file env_custom pull && docker-compose --env-file env_custom stop && docker-compose --env-file env_custom up -d`
