```php
<div :class="showDesktopSidebar ? 'flex flex-col' : 'flex flex-col items-center'" class="gap-y-1">
    @can('create', App\Models\StockIn::class)
        <x-nav-link :href="route('home')" :active="request()->routeIs('home') || request()->routeIs('home.*')">
            <x-slot name="svg">
                <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 4.5l-15 15m0 0h11.25m-11.25 0V8.25" />
            </x-slot>
            {{ __('အဝင်စာရင်းသွင်းခြင်း') }}
        </x-nav-link>
    @endcan

    @can('create', App\Models\Sale::class)
        <x-nav-link :href="route('sale.create')" :active="request()->routeIs('sale.createj') || request()->routeIs('sale.*')">
            <x-slot name="svg">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 19.5l15-15m0 0H8.25m11.25 0v11.25" />
            </x-slot>
            {{ __('အရောင်းစာရင်းသွင်းခြင်း') }}
        </x-nav-link>
    @endcan

    @can('view', App\Models\SalesCreditSettle::class)
        <x-nav-link :href="route('sales-credit-settle.index')" :active="request()->routeIs('sales-credit-settle.index') || request()->routeIs('sales-credit-settle.*')">
            <x-slot name="svg">
                <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 18.75a60.07 60.07 0 0115.797 2.101c.727.198 1.453-.342 1.453-1.096V18.75M3.75 4.5v.75A.75.75 0 013 6h-.75m0 0v-.375c0-.621.504-1.125 1.125-1.125H20.25M2.25 6v9m18-10.5v.75c0 .414.336.75.75.75h.75m-1.5-1.5h.375c.621 0 1.125.504 1.125 1.125v9.75c0 .621-.504 1.125-1.125 1.125h-.375m1.5-1.5H21a.75.75 0 00-.75.75v.75m0 0H3.75m0 0h-.375a1.125 1.125 0 01-1.125-1.125V15m1.5 1.5v-.75A.75.75 0 003 15h-.75M15 10.5a3 3 0 11-6 0 3 3 0 016 0zm3 0h.008v.008H18V10.5zm-12 0h.008v.008H6V10.5z" />
            </x-slot>
            {{ __('အကြွေးပြန်ဆပ်') }}
        </x-nav-link>
    @endcan

    @can('view', App\Models\UsedItemPurchase::class)
        <x-nav-link :href="route('used-item-purchase.index')" :active="request()->routeIs('used-item-purchase.index') || request()->routeIs('used-item-purchase.*')">
            <x-slot name="svg">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9 3.75H6.912a2.25 2.25 0 00-2.15 1.588L2.35 13.177a2.25 2.25 0 00-.1.661V18a2.25 2.25 0 002.25 2.25h15A2.25 2.25 0 0021.75 18v-4.162c0-.224-.034-.447-.1-.661L19.24 5.338a2.25 2.25 0 00-2.15-1.588H15M2.25 13.5h3.86a2.25 2.25 0 012.012 1.244l.256.512a2.25 2.25 0 002.013 1.244h3.218a2.25 2.25 0 002.013-1.244l.256-.512a2.25 2.25 0 012.013-1.244h3.859M12 3v8.25m0 0l-3-3m3 3l3-3" />
            </x-slot>
            {{ __('အထည်ဟောင်းဝယ်') }}
        </x-nav-link>
    @endcan

    @can('view', App\Models\ItemRepair::class)
        <x-nav-link :href="route('item-repair.index')" :active="request()->routeIs('item-repair.index') || request()->routeIs('item-repair.*')">
            <x-slot name="svg">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9.813 15.904L9 18.75l-.813-2.846a4.5 4.5 0 00-3.09-3.09L2.25 12l2.846-.813a4.5 4.5 0 003.09-3.09L9 5.25l.813 2.846a4.5 4.5 0 003.09 3.09L15.75 12l-2.846.813a4.5 4.5 0 00-3.09 3.09zM18.259 8.715L18 9.75l-.259-1.035a3.375 3.375 0 00-2.455-2.456L14.25 6l1.036-.259a3.375 3.375 0 002.455-2.456L18 2.25l.259 1.035a3.375 3.375 0 002.456 2.456L21.75 6l-1.035.259a3.375 3.375 0 00-2.456 2.456zM16.894 20.567L16.5 21.75l-.394-1.183a2.25 2.25 0 00-1.423-1.423L13.5 18.75l1.183-.394a2.25 2.25 0 001.423-1.423l.394-1.183.394 1.183a2.25 2.25 0 001.423 1.423l1.183.394-1.183.394a2.25 2.25 0 00-1.423 1.423z" />
            </x-slot>
            {{ __('အထည်ပြုပြင်') }}
        </x-nav-link>
    @endcan

    {{-- @can('view', App\Models\GoldsmithGoldDeposit::class)
        <x-nav-link :href="route('gold-deposit.index')" :active="request()->routeIs('gold-deposit.index') || request()->routeIs('gold-deposit.*')">
            <x-slot name="svg">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 3v17.25m0 0c-1.472 0-2.882.265-4.185.75M12 20.25c1.472 0 2.882.265 4.185.75M18.75 4.97A48.416 48.416 0 0012 4.5c-2.291 0-4.545.16-6.75.47m13.5 0c1.01.143 2.01.317 3 .52m-3-.52l2.62 10.726c.122.499-.106 1.028-.589 1.202a5.988 5.988 0 01-2.031.352 5.988 5.988 0 01-2.031-.352c-.483-.174-.711-.703-.59-1.202L18.75 4.971zm-16.5.52c.99-.203 1.99-.377 3-.52m0 0l2.62 10.726c.122.499-.106 1.028-.589 1.202a5.989 5.989 0 01-2.031.352 5.989 5.989 0 01-2.031-.352c-.483-.174-.711-.703-.59-1.202L5.25 4.971z" />
            </x-slot>
            {{ __('ပန်းထိမ်ရွှေအပ်') }}
        </x-nav-link>
    @endcan --}}

    @can('view', App\Models\Customer::class)
        <x-nav-link :href="route('customer.index')" :active="request()->routeIs('customer.index') || request()->routeIs('customer.*')">
            <x-slot name="svg">
                <path stroke-linecap="round" stroke-linejoin="round" d="M18 18.72a9.094 9.094 0 003.741-.479 3 3 0 00-4.682-2.72m.94 3.198l.001.031c0 .225-.012.447-.037.666A11.944 11.944 0 0112 21c-2.17 0-4.207-.576-5.963-1.584A6.062 6.062 0 016 18.719m12 0a5.971 5.971 0 00-.941-3.197m0 0A5.995 5.995 0 0012 12.75a5.995 5.995 0 00-5.058 2.772m0 0a3 3 0 00-4.681 2.72 8.986 8.986 0 003.74.477m.94-3.197a5.971 5.971 0 00-.94 3.197M15 6.75a3 3 0 11-6 0 3 3 0 016 0zm6 3a2.25 2.25 0 11-4.5 0 2.25 2.25 0 014.5 0zm-13.5 0a2.25 2.25 0 11-4.5 0 2.25 2.25 0 014.5 0z" />
            </x-slot>
            {{ __('ဝယ်သူ') }}
        </x-nav-link>
    @endcan

    @can('view', App\Models\Supplier::class)
        <x-nav-link :href="route('supplier.index')" :active="request()->routeIs('supplier.index') || request()->routeIs('supplier.*')">
            <x-slot name="svg">
                <path stroke-linecap="round" stroke-linejoin="round" d="M15 19.128a9.38 9.38 0 002.625.372 9.337 9.337 0 004.121-.952 4.125 4.125 0 00-7.533-2.493M15 19.128v-.003c0-1.113-.285-2.16-.786-3.07M15 19.128v.106A12.318 12.318 0 018.624 21c-2.331 0-4.512-.645-6.374-1.766l-.001-.109a6.375 6.375 0 0111.964-3.07M12 6.375a3.375 3.375 0 11-6.75 0 3.375 3.375 0 016.75 0zm8.25 2.25a2.625 2.625 0 11-5.25 0 2.625 2.625 0 015.25 0z" />
            </x-slot>
            {{ __('ပေးသွင်းသူ') }}
        </x-nav-link>
    @endcan

    @can('view', App\Models\User::class)
        <x-nav-link :href="route('user.index')" :active="request()->routeIs('user.index') || request()->routeIs('user.*')">
            <x-slot name="svg">
                <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 6a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0zM4.501 20.118a7.5 7.5 0 0114.998 0A17.933 17.933 0 0112 21.75c-2.676 0-5.216-.584-7.499-1.632z" />
            </x-slot>
            {{ __('အသုံးပြုသူ') }}
        </x-nav-link>
    @endcan

    @can('view roles')
        <x-nav-link :href="route('role-and-permission.index')" :active="request()->routeIs('role-and-permission.index') || request()->routeIs('role-and-permission.*')">
            <x-slot name="svg">
                <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 5.25a3 3 0 013 3m3 0a6 6 0 01-7.029 5.912c-.563-.097-1.159.026-1.563.43L10.5 17.25H8.25v2.25H6v2.25H2.25v-2.818c0-.597.237-1.17.659-1.591l6.499-6.499c.404-.404.527-1 .43-1.563A6 6 0 1121.75 8.25z" />
            </x-slot>
            {{ __('အသုံးပြုခွင့်') }}
        </x-nav-link>
    @endcan

    @can('view reports')
        <x-nav-link :href="route('report.index')" :active="request()->routeIs('report.index') || request()->routeIs('report.*')">
            <x-slot name="svg">
                <path stroke-linecap="round" stroke-linejoin="round" d="M3 13.125C3 12.504 3.504 12 4.125 12h2.25c.621 0 1.125.504 1.125 1.125v6.75C7.5 20.496 6.996 21 6.375 21h-2.25A1.125 1.125 0 013 19.875v-6.75zM9.75 8.625c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125v11.25c0 .621-.504 1.125-1.125 1.125h-2.25a1.125 1.125 0 01-1.125-1.125V8.625zM16.5 4.125c0-.621.504-1.125 1.125-1.125h2.25C20.496 3 21 3.504 21 4.125v15.75c0 .621-.504 1.125-1.125 1.125h-2.25a1.125 1.125 0 01-1.125-1.125V4.125z" />
            </x-slot>
            {{ __('စာရင်းများ') }}
        </x-nav-link>
    @endcan
</div>
```