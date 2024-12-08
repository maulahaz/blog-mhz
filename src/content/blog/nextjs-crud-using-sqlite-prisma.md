---
title: Next JS CRUD Using Sqlite and Prisma
author: MHz
pubDatetime: 2024-12-05T09:20:00Z
slug: nextjs-crud-using-sqlite-prisma
featured: true
draft: false
tags:
  - nextjs
  - prisma
  - sqlite
ogImage: ""
description: An Alternative way to do CRUD in Next JS 
canonicalURL: ""
---

#### 1. Install Dependencies
```
 //--Next, install Prisma and SQLite3:
	npm install prisma --save-dev
	npm install @prisma/client sqlite3
	
//--Initialize Prisma
	npx prisma init
	
	//-->This will create a prisma directory with a schema.prisma file.
```
#### 2. Configure the Prisma Schema
Edit the prisma/schema.prisma file to define your data model. For this example, let's create a simple Post model.
```
//--prisma/schema.prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "sqlite"
  url      = "file:./dev.db"
}

model Post {
  id      Int     @id @default(autoincrement())
  title   String
  content String
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}
```
#### 3. Migrate the Database
Run the following command to create the SQLite database and the Post table:
```
npx prisma migrate dev --name init
```
#### 4. Generate Prisma Client
Generate the Prisma Client to interact with the database:
```
npx prisma generate
```
#### 5. Create API Routes
Now, create API routes for the CRUD operations. Create a new folder under pages/api called posts, and inside that folder, create a file named index.js.
```
mkdir -p pages/api/posts
touch pages/api/posts/index.js
```
Edit pages/api/posts/index.js:
```
//-- pages/api/posts/index.js
import { PrismaClient } from '@prisma/client';

const prisma = new PrismaClient();

//-- GET all posts
const getPosts = async (req, res) => {
  const posts = await prisma.post.findMany();
  res.status(200).json(posts);
};

//-- CREATE a new post
const createPost = async (req, res) => {
  const { title, content } = req.body;
  const newPost = await prisma.post.create({
    data: {
      title,
      content,
    },
  });
  res.status(201).json(newPost);
};

//--Main API handler
export default async function handler(req, res) {
  if (req.method === 'GET') {
    return getPosts(req, res);
  } else if (req.method === 'POST') {
    return createPost(req, res);
  } else {
    res.setHeader('Allow', ['GET', 'POST']);
    res.status(405).end(`Method ${req.method} Not Allowed`);
  }
}
```
#### 6. Create a Dynamic API Route for Individual Posts
Create a new file named [id].js in the pages/api/posts folder for handling individual post operations:
```
touch pages/api/posts/[id].js
```
Edit pages/api/posts/[id].js:
```
//-- pages/api/posts/[id].js
import { PrismaClient } from '@prisma/client';

const prisma = new PrismaClient();

//-- GET a single post
const getPost = async (req, res) => {
  const { id } = req.query;
  const post = await prisma.post.findUnique({
    where: { id: Number(id) },
  });
  if (!post) {
    return res.status(404).json({ error: 'Post not found' });
  }
  res.status(200).json(post);
};

//-- UPDATE a post
const updatePost = async (req, res) => {
  const { id } = req.query;
  const { title, content } = req.body;
  const updatedPost = await prisma.post.update({
    where: { id: Number(id) },
    data: { title, content },
  });
  res.status(200).json(updatedPost);
};

//-- DELETE a post
const deletePost = async (req, res) => {
  const { id } = req.query;
  await prisma.post.delete({
    where: { id: Number(id) },
  });
  res.status(204).end();
};

//-- Main API handler
export default async function handler(req, res) {
  if (req.method === 'GET') {
    return getPost(req, res);
  } else if (req.method === 'PUT') {
    return updatePost(req, res);
  } else if (req.method === 'DELETE') {
    return deletePost(req, res);
  } else {
    res.setHeader('Allow', ['GET', 'PUT', 'DELETE']);
    res.status(405).end(`Method ${req.method} Not Allowed`);
  }
}
```
#### 7. Create the Frontend
Now, let's create a simple UI to interact with our API. Edit pages/index.js:
```
//-- pages/index.js
import { useEffect, useState } from 'react';

export default function Home() {
  const [posts, setPosts] = useState([]);
  const [title, setTitle] = useState('');
  const [content, setContent] = useState('');

  const fetchPosts = async () => {
    const res = await fetch('/api/posts');
    const data = await res.json();
    setPosts(data);
  };

  const createPost = async (e) => {
    e.preventDefault();
    const res = await fetch('/api/posts', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ title, content }),
    });
    if (res.ok) {
      fetchPosts();
      setTitle('');
      setContent('');
    }
  };

  const deletePost = async (id) => {
    await fetch(`/api/posts/${id}`, {
      method: 'DELETE',
    });
    fetchPosts();
  };

  useEffect(() => {
    fetchPosts();
  }, []);

  return (
    <div>
      <h1>Posts</h1>
      <form onSubmit={createPost}>
        <input
          type="text"
          placeholder="Title"
          value={title}
          onChange={(e) => setTitle(e.target.value)}
          required
        />
        <textarea
          placeholder="Content"
          value={content}
          onChange={(e) => setContent(e.target.value)}
          required
        />
        <button type="submit">Create Post</button>
      </form>
      <ul>
        {posts.map((post) => (
          <li key={post.id}>
            <h2>{post.title}</h2>
            <p>{post.content}</p>
            <button onClick={() => deletePost(post.id)}>Delete</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
```
#### 8. Run Your Application
Finally, start your Next.js application:
```
npm run dev
```
---
ALTERNATIVE WAY
===
#### 4. Set Up API Routes for CRUD Operations
- Create a new folder for API routes: Create a directory named pages/api/posts and add the following files for handling CRUD operations.

- Create pages/api/posts/index.js for handling GET and POST requests:

```
//-- pages/api/posts/index.js
import { PrismaClient } from '@prisma/client';

const prisma = new PrismaClient();

export default async function handler(req, res) {
  if (req.method === 'GET') {
    // Retrieve all posts
    const posts = await prisma.post.findMany();
    res.status(200).json(posts);
  } else if (req.method === 'POST') {
    // Create a new post
    const { title, content } = req.body;
    const newPost = await prisma.post.create({
      data: {
        title,
        content,
      },
    });
    res.status(201).json(newPost);
  } else {
    res.setHeader('Allow', ['GET', 'POST']);
    res.status(405).end(`Method ${req.method} Not Allowed`);
  }
}
```

- Create pages/api/posts/[id].js for handling GET, PUT, and DELETE requests for a specific post:

```
//-- pages/api/posts/[id].js
import { PrismaClient } from '@prisma/client';

const prisma = new PrismaClient();

export default async function handler(req, res) {
  const { id } = req.query;

  if (req.method === 'GET') {
    // Retrieve a specific post
    const post = await prisma.post.findUnique({
      where: { id: Number(id) },
    });
    res.status(200).json(post);
  } else if (req.method === 'PUT') {
    // Update a specific post
    const { title, content } = req.body;
    const updatedPost = await prisma.post.update({
      where: { id: Number(id) },
      data: { title, content },
    });
    res.status(200).json(updatedPost);
  } else if (req.method === 'DELETE') {
    // Delete a specific post
    await prisma.post.delete({
      where: { id: Number(id) },
    });
    res.status(204).end();
  } else {
    res.setHeader('Allow', ['GET', 'PUT', 'DELETE']);
    res.status(405).end(`Method ${req.method} Not Allowed`);
  }
}
```
#### 5. Create a Simple Frontend for Testing CRUD Operations
- Edit pages/index.js to create a simple UI for testing the CRUD operations:

```
//-- pages/index.js
import { useEffect, useState } from 'react';

export default function Home() {
  const [posts, setPosts] = useState([]);
  const [title, setTitle] = useState('');
  const [content, setContent] = useState('');

  useEffect(() => {
    fetchPosts();
  }, []);

  const fetchPosts = async () => {
    const res = await fetch('/api/posts');
    const data = await res.json();
    setPosts(data);
  };

  const createPost = async () => {
    await fetch('/api/posts', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ title, content }),
    });
    setTitle('');
    setContent('');
    fetchPosts();
  };

  const deletePost = async (id) => {
    await fetch(`/api/posts/${id}`, {
      method: 'DELETE',
    });
    fetchPosts();
  };

  return (
    <div>
      <h1>Posts</h1>
      <input
        type="text"
        placeholder="Title"
        value={title}
        onChange={(e) => setTitle(e.target.value)}
      />
      <textarea
        placeholder="Content"
        value={content}
        onChange={(e) => setContent(e.target.value)}
      />
      <button onClick={createPost}>Create Post</button>
      <ul>
        {posts.map((post) => (
          <li key={post.id}>
            <h2>{post.title}</h2>
            <p>{post.content}</p>
            <button onClick={() => deletePost(post.id)}>Delete</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
```
#### 6. Run Your Application
