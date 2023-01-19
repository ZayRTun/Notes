```php
@props(['active'])

@php
    $classes = $active ?? false ? 'bg-gradient-to-t from-yellow-400 via-yellow-300 to-yellow-200 group flex items-center px-2 py-2 text-sm font-medium rounded-md hover:from-yellow-500 hover:to-yellow-200' : 'text-gray-600 hover:bg-gray-100 group flex items-center px-2 py-2 text-sm font-medium rounded-md';
    $classesCollapsed = $active ?? false ? 'bg-gradient-to-t from-yellow-400 via-yellow-300 to-yellow-200 group inline-flex items-center justify-center px-2 py-2 text-sm font-medium rounded-md hover:from-yellow-500 hover:to-yellow-200' : 'text-gray-600 hover:bg-gray-100 group inline-flex items-center justify-center px-2 py-2 text-sm font-medium rounded-md';
    
    $svgClasses = $active ?? false ? 'mr-3 flex-shrink-0 h-6 w-6' : 'text-gray-500 mr-3 flex-shrink-0 h-6 w-6';
    $svgClassesCollapsed = $active ?? false ? 'flex-shrink-0 h-6 w-6' : 'text-gray-500 flex-shrink-0 h-6 w-6';
@endphp

<a x-show="showDesktopSidebar" {{ $attributes->merge(['class' => $classes]) }}>
    @isset($svg)
        <svg {{ $attributes->merge(['class' => $svgClasses]) }} xmlns="http://www.w3.org/2000/svg" fill="none"
            viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
            {{ $svg }}
        </svg>
    @endisset
    {{ $slot }}
</a>

<a x-show="!showDesktopSidebar" {{ $attributes->merge(['class' => $classesCollapsed]) }}>
    @isset($svg)
        <svg {{ $attributes->merge(['class' => $svgClassesCollapsed]) }} xmlns="http://www.w3.org/2000/svg" fill="none"
            viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
            {{ $svg }}
        </svg>
    @endisset
</a>

```