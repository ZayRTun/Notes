```php
<div x-data="{ showOffCanvasMenu: false, showDropDownMenu: false, showDesktopSidebar: $persist(true), showGoldRateModal: false }">
    {{-- Mobile off Canvas Menu --}}
    <div
        x-cloak
        x-show="showOffCanvasMenu"
        x-transition:enter="transition-opacity ease-linear duration-300"
        x-transition:enter-start="opacity-0"
        x-transition:enter-end="opacity-100"
        x-transition:leave="transition-opacity ease-linear duration-300"
        x-transition:leave-start="opacity-100"
        x-transition:leave-end="opacity-0"
        class="relative z-40 md:hidden" role="dialog" aria-modal="true">

        <div class="fixed inset-0 bg-gray-600 bg-opacity-75"></div>

        <div
            x-show="showOffCanvasMenu"
            x-transition:enter="transition ease-in-out duration-300 transform"
            x-transition:enter-start="-translate-x-full"
            x-transition:enter-end="translate-x-0"
            x-transition:leave="transition ease-in-out duration-300 transform"
            x-transition:leave-start="translate-x-0"
            x-transition:leave-end="-translate-x-full"
            class="fixed inset-0 z-40 flex">

            <div
                @click.outside="showOffCanvasMenu = false"
                x-show="showOffCanvasMenu"
                x-transition:enter="ease-in-out duration-300"
                x-transition:enter-start="opacity-0"
                x-transition:enter-end="opacity-100"
                x-transition:leave="ease-in-out duration-300"
                x-transition:leave-start="opacity-100"
                x-transition:leave-end="opacity-0"
                class="relative flex w-full max-w-xs flex-1 flex-col bg-white">


                <div class="absolute top-0 right-0 -mr-12 pt-2">
                    <button
                        @click="showOffCanvasMenu = false"
                        type="button"
                        class="ml-1 flex h-10 w-10 items-center justify-center rounded-full focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white">
                        <span class="sr-only">Close sidebar</span>
                        <!-- Heroicon name: outline/x-mark -->
                        <svg class="h-6 w-6 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                            stroke-width="1.5" stroke="currentColor" aria-hidden="true">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                        </svg>
                    </button>
                </div>

                <div class="h-0 flex-1 overflow-y-auto pt-5 pb-4">
                    <div class="flex flex-shrink-0 items-center px-4">
                        <h1 class="text-gray-900 text-lg">{{ config('app.name') }}</h1>
                        {{-- <img class="h-8 w-auto" src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=500" alt="Your Company"> --}}
                    </div>
                    <nav class="mt-5 space-y-1 px-2">
                        <x-navigation />
                    </nav>
                </div>

                <div class="flex flex-shrink-0 border-t border-gray-200 p-4">
                    <a href="#" class="group block flex-shrink-0">
                        <div class="flex items-center">
                            <div>
                                <img class="inline-block h-10 w-10 rounded-full"
                                    src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                                    alt="">
                            </div>
                            <div class="ml-3">
                                <p class="text-base font-medium text-gray-700 group-hover:text-gray-900">Tom Cook</p>
                                <p class=" font-medium text-gray-500 group-hover:text-gray-700">View profile</p>
                            </div>
                        </div>
                    </a>
                </div>
            </div>

            <div class="w-14 flex-shrink-0">
                <!-- Force sidebar to shrink to fit close icon -->
            </div>
        </div>
    </div>
    {{-- End Of Mobile off canvas menu --}}


    {{-- Static sidebar for desktop --}}
    <div x-cloak :class="showDesktopSidebar ? 'md:w-64' : 'md:w-[4rem]'" class="hidden md:fixed md:inset-y-0 md:flex md:flex-col z-[1000]">
        <!-- Sidebar component, swap this element with another sidebar if you like -->
        <div class="flex min-h-0 flex-1 flex-col border-r border-gray-200 bg-white">

            <div class="flex flex-1 flex-col overflow-y-auto pt-3 pb-4">
                <div class="flex flex-shrink-0 items-center px-4" :class="showDesktopSidebar ? 'justify-between' : 'justify-center'">
                    <h1 x-show="showDesktopSidebar" class="text-gray-900 text-lg text-center font-normal leading-none">{{ config('app.name') }}</h1>
                    <x-sidebar-toggle-button x-on:click="showDesktopSidebar = !showDesktopSidebar" />
                </div>

                <nav wire:ignore class="mt-5 flex-1 bg-white px-3 text-center">
                    <x-navigation />
                </nav>
            </div>



            {{-- Gold Rate / Change Password and Log Out  --}}
            <div class="flex flex-shrink-0 flex-col  space-y-3 border-t border-gray-200" :class="showDesktopSidebar ? 'px-3 py-4' : 'px-3 py-4 items-center'">
                <div class="flex items-center space-x-3">
                    <button @click="showGoldRateModal = ! showGoldRateModal" type="button" class="group relative inline-flex h-5 w-10 flex-shrink-0 cursor-pointer items-center justify-center rounded-full focus:outline-none focus:ring-2 focus:ring-yellow-300 focus:ring-offset-2" role="switch" aria-checked="false">
                        <span aria-hidden="true" class="pointer-events-none absolute h-full w-full rounded-md bg-white"></span>
                        <span aria-hidden="true" :class="showGoldRateModal ? 'bg-yellow-400' : 'bg-gray-200'" class="pointer-events-none absolute mx-auto h-4 w-9 rounded-full transition-colors duration-200 ease-in-out"></span>
                        <span aria-hidden="true" :class="showGoldRateModal ? 'translate-x-5' : 'translate-x-0'" class="pointer-events-none absolute left-0 inline-block h-5 w-5 transform rounded-full border border-gray-200 bg-white shadow ring-0 transition-transform duration-200 ease-in-out"></span>
                    </button>

                    <span :class="showDesktopSidebar ? 'inline-block' : 'hidden'" class="text-sm font-medium text-gray-700 group-hover:text-gray-900" @click="showGoldRateModal = ! showGoldRateModal">
                        {{ __('ရွှေဈေး') }}
                    </span>
                </div>

                <!-- Profile dropdown -->
                <x-profile-dropdown>
                    <button type="button" wire:click="$emit('updateAppSetting')"
                        class="w-full text-left px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 focus:outline-none focus:bg-gray-100 transition duration-150 ease-in-out">
                        App Settings
                    </button>

                    <button type="button" wire:click="$emit('changePassword', '{{ auth()->id() }}')"
                        class="w-full text-left px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 focus:outline-none focus:bg-gray-100 transition duration-150 ease-in-out">
                        Change Password
                    </button>

                    <form method="POST" action="{{ route('logout') }}">
                        @csrf
                        <x-dropdown-link role="menuitem" tabindex="-1" :href="route('logout')" onclick="event.preventDefault(); this.closest('form').submit();">
                            {{ __('Sign Out') }}
                        </x-dropdown-link>
                    </form>
                </x-profile-dropdown>

            </div>
            {{-- End of profile --}}
        </div>
    </div>
    {{-- End of Static sidebar for desktop --}}


    {{-- Right Side Content --}}
    <div x-cloak :class="showDesktopSidebar ? 'md:pl-64' : 'md:pl-16'" class="flex flex-1 flex-col h-screen">
        <div class="sticky top-0 z-10 bg-white pl-1 pt-1 sm:pl-3 sm:pt-3 md:hidden">
            <button
                @click="showOffCanvasMenu = true"
                type="button"
                class="-ml-0.5 -mt-0.5 inline-flex h-12 w-12 items-center justify-center rounded-md text-gray-500 hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-500">
                <span class="sr-only">Open sidebar</span>
                <!-- Heroicon name: outline/bars-3 -->
                <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                    stroke="currentColor" aria-hidden="true">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
                </svg>
            </button>
        </div>


        {{-- Main Content --}}
        @php
            $font_size = app('Setting')->font_size;
        @endphp
        <main @class([
            'flex-1',
            'text-sm' => $font_size == 1,
            'text-base' => $font_size == 2,
            'text-lg' => $font_size == 3,
        ])>
            <div class="py-3">
                <div class="mx-auto max-w-full px-4 sm:px-6 lg:px-8">
                    {{ $slot }}
                </div>
            </div>
        </main>
        {{-- End of Main Content --}}
    </div>
    {{-- End of Right Side Content --}}
</div>
```