# Nango-Github-Jira-report

  
This project integrates GitHub and Jira using Nango to fetch user data from both platforms and generate combined reports. It provides a web interface for users to log in with Google, authorize access to their GitHub and Jira accounts, and receive a consolidated report of their activities on both platforms.  
  
## Table of Contents  
  
- [Features](#features)  
- [Prerequisites](#prerequisites)  
- [Installation](#installation)  
- [Usage](#usage)  
 
  
## Features  
  
- Google SSO for user authentication  
- GitHub OAuth integration to fetch user repositories, issues, and pull requests  
- Jira OAuth integration to fetch user projects and issues  
- Combined report generation in PDF format using OpenAI's language model  
- Daily data synchronization using cron jobs  
  
## Prerequisites  
  
Before you begin, ensure you have met the following requirements:  
  
- Node.js and npm installed on your machine  
- MongoDB instance running  
- GitHub and Jira developer accounts for OAuth integration  
- Google Developer Console credentials for SSO  
- Azure OpenAI service credentials  
  
## Installation  
  
1. Clone the repository:  
  
    ```sh  
    git clone https://github.com/your-username/nango-github-jira-integration.git  
    cd nango-github-jira-integration  
    ```  
  
2. Install dependencies:  
  
    ```sh  
    npm install  
    ```  
  
3. Set up environment variables:  
  
    Create a `.env` file in the root directory and add the following variables:  
  
    ```env  
    PORT=3001  
    GITHUB_CLIENT_ID=your_github_client_id  
    GITHUB_CLIENT_SECRET=your_github_client_secret  
    GITHUB_REDIRECT_URI=http://localhost:3001/oauth/github/callback  
    MONGODB_URI=mongodb://localhost:27017/  
    AZURE_OPENAI_ENDPOINT=https://jira-work.openai.azure.com  
    AZURE_TENANT_ID=your_azure_tenant_id  
    AZURE_CLIENT_ID=your_azure_client_id  
    AZURE_CLIENT_SECRET=your_azure_client_secret  
    AZURE_SUBSCRIPTION_ID=your_azure_subscription_id  
    JIRA_CLIENT_ID=your_jira_client_id  
    JIRA_CLIENT_SECRET=your_jira_client_secret  
    JIRA_REDIRECT_URI=http://localhost:3001/oauth/jira/callback  
    GOOGLE_CLIENT_ID=your_google_client_id  
    GOOGLE_CLIENT_SECRET=your_google_client_secret  
    ```  
  
4. Configure Nango:  
  
    Create a `nango.yml` file in the root directory and add the following configuration:  
  
    ```yaml  
    integrations:  
      - name: github  
        provider: github  
        client_id: ${GITHUB_CLIENT_ID}  
        client_secret: ${GITHUB_CLIENT_SECRET}  
        redirect_uri: ${GITHUB_REDIRECT_URI}  
        scopes:  
          - repo  
          - user  
          - read:org  
          - read:repo_hook  
          - read:issues  
          - read:pull_request  
    ```  
  
## Usage  
  
1. Start the server:  
  
    ```sh  
    npm start  
    ```  
  
2. Open your web browser and navigate to `http://localhost:3001`.  
  
3. Log in with your Google account.  
  
4. Authorize access to your GitHub account.  
  
5. Authorize access to your Jira account.  
  
6. A combined report of your GitHub and Jira activities will be generated and displayed.  
  
