<template>
  <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 py-8">
	  <div class="border-b border-gray-300 pb-4 md:flex md:items-center md:justify-between">
		  <div class="min-w-0 flex-1">
			  <h2 class="text-2xl font-bold leading-7 text-gray-900 sm:truncate sm:text-3xl sm:tracking-tight">Tiptap sandbox</h2>
		  </div>
		  <div class="mt-4 flex md:ml-4 md:mt-0">
			  <a href="https://tiptap.dev/introduction" target="_blank" class="inline-flex items-center rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50">Documentation</a>
		  </div>
	  </div>
    <div class="py-4">
      <slot />
    </div>
    <div class="py-4 border-t border-gray-300">
      <p class="mt-2 text-sm font-light text-gray-500">Tool by Jacob Fitzpatrick</p>
    </div>
  </div>
</template>
