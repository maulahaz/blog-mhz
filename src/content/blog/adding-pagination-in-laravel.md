---
title: Adding pagination in Laravel
author: MHz
pubDatetime: 2025-06-07T12:25:00Z
slug: adding-pagination-in-laravel
featured: true
draft: false
tags:
  - Laravel
  - Pagination
  - Bootstrap
  - AdminLTE
ogImage: ""
description: Adding Bootstrap Pagination in Laravel 10
canonicalURL: ""
---

# Adding pagination in Laravel
To add Pagination in the Penduduk index view, we need to modify both the controller and the view. We'll set it to display 20 rows per page. Here's how to do it:
1. First, let's update the index method in the PendudukController:
```
public function index()
{
    $this->data['pageTitle'] = 'Data Penduduk';
    $this->data['penduduks'] = Penduduk::paginate(20);
    return view('admin.penduduk.index', $this->data);
}
```

2. Now, let's update the view to display the pagination links. Add this just after the table in the index.blade.php file:
```
<div class="card-body table-responsive p-0">
    <table class="table table-hover text-nowrap">
        <!-- ... existing table code ... -->
    </table>
</div>
<div class="card-footer clearfix">
    {{ $penduduks->links() }}
</div>
```

3. To ensure the pagination links are styled correctly with AdminLTE, you might need to publish the Laravel pagination views and modify them. Run this command:
```
php artisan vendor:publish --tag=laravel-pagination
```
4. 
Then, edit the file resources/views/vendor/pagination/bootstrap-4.blade.php to style it according to AdminLTE. Here's an example of how you might modify it:
```
@if ($paginator->hasPages())
<nav>
    <ul class="pagination">
        {{-- Previous Page Link --}}
        @if ($paginator->onFirstPage())
        <li class="page-item disabled" aria-disabled="true" aria-label="@lang('pagination.previous')">
            <span class="page-link" aria-hidden="true">&lsaquo;</span>
        </li>
        @else
        <li class="page-item">
            <a class="page-link" href="{{ $paginator->previousPageUrl() }}" rel="prev" aria-label="@lang('pagination.previous')">&lsaquo;</a>
        </li>
        @endif

        {{-- Pagination Elements --}}
        @foreach ($elements as $element)
        {{-- "Three Dots" Separator --}}
        @if (is_string($element))
        <li class="page-item disabled" aria-disabled="true"><span class="page-link">{{ $element }}</span></li>
        @endif

        {{-- Array Of Links --}}
        @if (is_array($element))
        @foreach ($element as $page => $url)
        @if ($page == $paginator->currentPage())
        <li class="page-item active" aria-current="page"><span class="page-link">{{ $page }}</span></li>
        @else
        <li class="page-item"><a class="page-link" href="{{ $url }}">{{ $page }}</a></li>
        @endif
        @endforeach
        @endif
        @endforeach

        {{-- Next Page Link --}}
        @if ($paginator->hasMorePages())
        <li class="page-item">
            <a class="page-link" href="{{ $paginator->nextPageUrl() }}" rel="next" aria-label="@lang('pagination.next')">&rsaquo;</a>
        </li>
        @else
        <li class="page-item disabled" aria-disabled="true" aria-label="@lang('pagination.next')">
            <span class="page-link" aria-hidden="true">&rsaquo;</span>
        </li>
        @endif
    </ul>
</nav>
@endif
```
5. Call the paginator's useBootstrapFour or useBootstrapFive methods within the boot method of your App\Providers\AppServiceProvider class:
```
use Illuminate\Pagination\Paginator;
 
/**
 * Bootstrap any application services.
 */
public function boot(): void
{
    Paginator::useBootstrapFive();
    Paginator::useBootstrapFour();
}
```
