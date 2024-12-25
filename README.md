# Custom-AI-Jira-Agent 
A chat interface to interact with Jira via an AI agent, with a custom AI agent tool to triage newly created Jira tickets.

The project makes use of LangChain agents, served via Django (with PostgreSQL) and Google Mesop. Services are provided in Docker to be run locally. 
The prompting strategy includes a CO-STAR system prompt, Chain-of-Thought (CoT) reasoning with few-shot prompting.
The inspiration for this project came from hosting a Jira ticket creation tool on a web application I had developed for internal users. I also added automated Jira ticket creation upon system errors. 
Users and system errors often create similar tickets, so I wanted to see if the reasoning capabilities of LLMs could be used to automatically triage tickets by linking related issues, creating user stories, acceptance criteria, and priority.

The inspiration for this project came from hosting a Jira ticket creation tool on a web application I had developed for internal users. I also added automated Jira ticket creation upon system errors. 
Users and system errors often create similar tickets, so I wanted to see if the reasoning capabilities of LLMs could be used to automatically triage tickets by linking related issues, creating user stories, acceptance criteria, and priority.
Additionally, giving users and product/ managerial stakeholders easier access to interact directly with Jira in natural language without any technical competencies was an interesting prospect.

For more information, please read the medium article here. 

![Custom AI Jira agent demo](https://github.com/user-attachments/assets/5d8b0a22-6673-408b-80c8-c1d28a83380a)

## What is Google Mesop?
Mesop is a relatively recent (2023) Python web framework used at Google for rapid AI app development.
"Mesop provides a versatile range of 30 components, from low-level building blocks to high-level, AI-focused components. 
This flexibility lets you rapidly prototype ML apps or build custom UIs, all within a single framework that adapts to your project's use case." - [Mesop Homepage](https://google.github.io/mesop/)

## What is an AI Agent? 
"An artificial intelligence (AI) agent is a software program that can interact with its environment, collect data, and use the data to perform self-determined tasks to meet predetermined goals.
Humans set goals, but an AI agent independently chooses the best actions it needs to perform to achieve those goals.
AI agents are rational agents. They make rational decisions based on their perceptions and data to produce optimal performance and results.
An AI agent senses its environment with physical or software interfaces." - [AWS Website](https://aws.amazon.com/what-is/ai-agents/)

## What is CO-STAR prompting?
"The CO-STAR framework, a brainchild of GovTech Singapore's Data Science & AI team, is a handy template for structuring prompts.
It considers all the key aspects that influence the effectiveness and relevance of an LLM's response, leading to more optimal responses." - [Sheila Teo's Medium Post](https://towardsdatascience.com/how-i-won-singapores-gpt-4-prompt-engineering-competition-34c195a93d41)

## What is Chain of Thought (CoT) prompting? 
Originally proposed in a Google paper; [Wei et al. (2022)](https://arxiv.org/pdf/2201.11903). Chain-of-Thought (CoT) prompting means to provide few-shot prompting examples of intermediate reasoning steps. 
Which was proven to improve common-sense reasoning of the model output.

## What is Django? 
Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. 
Built by experienced developers, it takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. 
It's free and open source. - [Django Homepage](https://www.djangoproject.com/) 

## What is LangChain?
"LangChain's flexible abstractions and AI-first toolkit make it the #1 choice for developers when building with GenAI.
Join 1M+ builders standardizing their LLM app development in LangChain's Python and JavaScript frameworks." - [LangChain website](https://www.langchain.com/langchain)

## Run Locally  
First, you must add your Open AI API key and Jira credentials to the config file.  
```
./config/config.ini
```
Run the following.  
```
docker compose up --build 
```
Once docker is running, to see the Mesop UI - please navigate from your browser to the following URL:  
```
http://localhost:8080/
```
Once finished, be sure to run the following.
```
docker compose down
```

## Requirements  
Requires the following 
* Docker Desktop 
* Open AI API Key 
* JIRA API Token 
* Jira Username 
* Jira Instance URL 

## References 
* https://google.github.io/mesop/getting-started/quickstart/#starter-kit
* https://www.django-rest-framework.org/#example
* https://blog.logrocket.com/dockerizing-django-app/

## TODO 
* Add coding agent tool 