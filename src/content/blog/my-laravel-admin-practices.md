---
title: My Laravel-Admin Practices
author: MHz
pubDatetime: 2024-12-02T20:20:00Z
slug: my-laravel-admin-practices
featured: true
draft: false
tags:
  - laravel
ogImage: ""
description: Some notes from My Laravel-Admin Experience
canonicalURL: ""
---


#### To Reset Admin Password:
```
$ php artisan admin:reset-password

 Please enter a username who needs to reset his password:
 >

```

#### Make Controller in Admin Folder
```
1. Create Migration
2. Create Model: 
	$ php artisan make:model Lesson
3. Create Controller:
    //--Mac:
    $ php artisan admin:make LessonController --model=App\\Models\\Lesson
    //--Win:
    $ php artisan admin:make LessonController --model=App\Models\Lesson
4. Add Admin Routes link (App/Admin/routes.php):
	$router->resource('/lessons', LessonController::class);

```