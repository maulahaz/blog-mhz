---
title: Integrate Supabase with a PWA on Vercel
author: MHz
pubDatetime: 2024-12-08T09:25:00Z
slug: Integrate-Supabase-with-a-PWA-on-Vercel
featured: true
draft: false
tags:
  - Supabase
  - PWA
ogImage: ""
description: Integrating Supabase with a PWA deployed on Vercel
canonicalURL: ""
---

### How to:

1. Create a Supabase Project 
	- Go to Supabase
	- Create an account and then create a new project.
	- Once project is set up, configure the database, authentication, and any required APIs.
	
2. Get Supabase API Keys
	- After project created, go to the "Settings" section on the Supabase dashboard.
	- Under "API", find project URL and the API key. Keep these record to connect PWA to Supabase.
	
3. Set Up PWA
	- If PWA not yet created, use frameworks like React, Vue, or Angular, or even frameworks specifically designed for PWAs like Next.js or Svelte.
	- Create a new project using chosen framework.
	
4. Install Supabase Client
	```
	npm install @supabase/supabase-js
	```
	
5. Initialize Supabase in PWA
	- Create a new file (e.g., supabase.js) for Supabase client setup:
	```
	import { createClient } from '@supabase/supabase-js';
	
	const supabaseUrl = 'https://your-project-ref.supabase.co';
	const supabaseAnonKey = 'your-anon-public-key';
	
	export const supabase = createClient(supabaseUrl, supabaseAnonKey);
	```
	
6. Implement CRUD Operations
	- Use the Supabase client to perform CRUD operations in your app
	```
	// Example - Fetching data
const { data, error } = await supabase.from('your_table').select('*');
	
	// Example - Inserting data
const { data, error } = await supabase.from('your_table').insert([{ column1: 'value1', column2: 'value2' }]);
	```
	
7. Deploy on Vercel
	- Push project to a Git repository (GitHub, GitLab, etc.).
	- Go to Vercel and log in or sign up.
	- Click on "New Project" and select the repository.
	- Vercel will automatically detect the framework and configure the deployment settings.
	- Click on "Deploy" to publish the PWA.
	
8. Use Environment Variables (Optional)
	- **CORS**: Ensure that Supabase project allows requests from deployed PWA's domain.
	- **Service Workers**: If implementing service workers in the PWA, make sure to manage caching and API calls appropriately
