**Home**
- [Home](../index.md)
---

# Image preview Base64
```html
<div x-data="{ photoName: null, photoPreview: null }" class="col-span-6 sm:col-span-4">
                                <!-- Profile Photo File Input -->
<input type="file" class="hidden" wire:model="photo" x-ref="photo" x-on:change="
                    photoName = $refs.photo.files[0].name;
                    const reader = new FileReader();
                    reader.onload = (e) => {
                        console.log(e.target.result);
                        photoPreview = e.target.result;
                    };
                    reader.readAsDataURL($refs.photo.files[0]);
            ">

<label class="block font-medium text-sm text-gray-700" for="photo">
    Photo
</label>

<!-- Current Profile Photo -->
<div class="mt-2" x-show="! photoPreview">
    <img src="https://ui-avatars.com/api/?name={{ $user->name }}&amp;color=7F9CF5&amp;background=EBF4FF" alt="{{ $user->name }}" class="rounded-full h-20 w-20 object-cover">
</div>

<!-- New Profile Photo Preview -->
<div class="mt-2" x-show="photoPreview" style="display: none;">
    <span class="block rounded-full w-20 h-20"
        x-bind:style="'background-size: cover; background-repeat: no-repeat; background-position: center center; background-image: url(\'' + photoPreview + '\');'" style="background-size: cover; background-repeat: no-repeat; background-position: center center; background-image: url('null');">
    </span>
</div>

<button
    x-on:click.prevent="$refs.photo.click()"
    type="button"
    class="inline-flex items-center px-4 py-2 bg-white border border-gray-300 rounded-md font-semibold text-xs text-gray-700 uppercase tracking-widest shadow-sm hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:text-gray-800 active:bg-gray-50 transition ease-in-out duration-150 mt-2 mr-2">
    Select A New Photo
</button>
</div>
```
