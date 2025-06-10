---
title: Create free AI API from Openrouter
author: MHz
pubDatetime: 2025-06-08T18:25:00Z
slug: create-free-ai-api-from-openrouter
featured: true
draft: false
tags:
  - AI
  - Openrouter
  - Deepseek
ogImage: ""
description: Create free AI API (Deepseek) from Openrouter
canonicalURL: ""
---

### How to:

1. Open Web "openrouter.ai"
2. Type in Search box: DeepSeek R1 0528 (free)
3. Goto tab API and Click button "Create API Key"
4. Create a API Name (ex. api-deepseek-r1)
5. Click Create API Key, then it will generate API Key (ex. 649-xxx)
6. Note down API Name and API Key
7. For trial, let's make AI Chat App through v0.dev, Lovable.dev or others.
- Enter this prompt: "Build an AI Chat App and allow me to key in Deepseek API Key. Here is the Fetch example: [copy-paste the fetch code below]"
- When the Apps built, copy-paste the created API Key above (Remove MHZ code -- red)

## Fetch Code For Typescript:
```
fetch("https://openrouter.ai/api/v1/chat/completions", {
  method: "POST",
  headers: {
    "Authorization": "Bearer <OPENROUTER_API_KEY>",
    "HTTP-Referer": "<YOUR_SITE_URL>", // Optional. Site URL for rankings on openrouter.ai.
    "X-Title": "<YOUR_SITE_NAME>", // Optional. Site title for rankings on openrouter.ai.
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    "model": "deepseek/deepseek-r1-0528:free",
    "messages": [
      {
        "role": "user",
        "content": "What is the meaning of life?"
      }
    ]
  })
});
``` 
## Fetch Code For Python:
```
import requests
import json

response = requests.post(
  url="https://openrouter.ai/api/v1/chat/completions",
  headers={
    "Authorization": "Bearer <OPENROUTER_API_KEY>",
    "Content-Type": "application/json",
    "HTTP-Referer": "<YOUR_SITE_URL>", # Optional. Site URL for rankings on openrouter.ai.
    "X-Title": "<YOUR_SITE_NAME>", # Optional. Site title for rankings on openrouter.ai.
  },
  data=json.dumps({
    "model": "deepseek/deepseek-r1-0528:free",
    "messages": [
      {
        "role": "user",
        "content": "What is the meaning of life?"
      }
    ],
    
  })
)
``` 