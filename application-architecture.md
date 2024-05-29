# 🏗️ Application Architecture

## **Overall Architecture:**

This application follows a microservices architecture with two main components:

1. **Backend (Godel Flask API):**
   * Handles the core logic of interacting with the Large Language Model (LLM), specifically Microsoft's GODEL-v1\_1-base-seq2seq model.
   * **Environment Variables:** Retrieves configuration from environment variables (loaded from the ConfigMap in the Kubernetes setup).
   * Receives chat input from the frontend, processes it through the LLM, and returns a generated response.
   * Relies on the `transformers` library for LLM integration and `Flask` for the web framework.
   * Uses Flask for the web server and exposes a `/chat` endpoint to handle chat requests and a `/health` endpoint for health checks.
2. **Frontend (Flask Web App):**
   * Uses `requests` for sending HTTP requests to the backend and `Flask` for the web framework.
   * Sends user input to the backend's `/chat` endpoint and displays the response.
   * Uses Flask for the web server and Jinja2 for templating the chat interface.
   * Maintains chat history using server-side sessions to maintain chat history.
   * Indicates from what backend Pod the response came from

### **Interaction Flow:**

1. The user enters a message in the chat interface on the frontend.
2. Frontend sends the user's input to the backend's `/chat` endpoint as a JSON payload.
3. Backend receives the request, processes the input using the LLM, generates a response, and returns the response as JSON along with pod/node metadata.
4. Frontend receives the response, updates the chat history, and renders the updated chat interface with the new message.

<figure><img src=".gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

* **Kubernetes Cluster:**
  * **Master Node (Control Plane):** Include components like the API server, scheduler, and controller manager.
  * **Worker Nodes:** Depict multiple worker nodes.
* **Backend Deployment:**
  * **Pods:** Show one or more pods running the GODEL-based backend API.
  * **ClusterIP Service:** Indicate the service connecting to the backend pods internally.
* **Frontend Deployment:**
  * **Pods:** Show one or more pods running the Flask-based frontend web app.
  * **NodePort Service:** Illustrate the service exposing the frontend to external traffic via node ports.
  * **LoadBalancer Service (Optional):** If applicable, include this service for cloud-based load balancing.
* **ConfigMap:** Depict the ConfigMap storing LLM configuration data (instructions, knowledge base, parameters).

## &#x20;LLM Model - GODEL 1.1&#x20;

<figure><img src=".gitbook/assets/image (19) (1).png" alt=""><figcaption><p>GODEL (<strong>G</strong>rounded <strong>O</strong>pen <strong>D</strong>ialogu<strong>e</strong> <strong>L</strong>anguage Model), a large <strong>open-source,</strong> pre-trained language model for dialogue. </p></figcaption></figure>

<figure><img src=".gitbook/assets/image (16) (1).png" alt=""><figcaption></figcaption></figure>

It is parameterized with a Transformer-based encoder-decoder model and trained for response generation grounded in external text, which allows more effective fine-tuning on dialogue tasks that require conditioning the response on information that is external to the current conversation (e.g., a retrieved document). The pre-trained model can be efficiently fine-tuned and adapted to accomplish a new dialogues task with a handful of task-specific dialogues.

> @misc{\
> peng2022godel, \
> author = {Peng, Baolin and Galley, Michel and He, Pengcheng and Brockett, Chris and Liden, Lars and Nouri, Elnaz and Yu, Zhou and Dolan, Bill and Gao, Jianfeng}, \
> title = {GODEL: Large-Scale Pre-training for Goal-Directed Dialog}, \
> howpublished = {arXiv}, \
> year = {2022}, month = {June}, \
> url = {https://www.microsoft.com/en-us/research/publication/godel-large-scale-pre-training-for-goal-directed-dialog/}, }
