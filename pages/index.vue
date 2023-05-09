<template>
  <div class="">
    <div class="border border-gray-400 shadow rounded-lg">
      <div class="p-2 border-b border-gray-400 flex gap-2">
        <a
          v-for="item in toolbar"
          href="#"
          @click.prevent="item.callback"
          class="hover:text-rose-600"
        >
            <Icon size="1.75em" :name="item.icon" />
        </a>
      </div>
      <editor-content :editor="editor"></editor-content>
    </div>
    <h2 class="mt-4 text-lg font-semibold">Output <Icon class="cursor-pointer hover:text-gray-500" name="material-symbols:content-copy" /></h2>
    <pre class="mt-4 border-l-4 pl-4 border-gray-300 text-xs">{{ content }}</pre>
  </div>
</template>

<script>
import { Editor, EditorContent } from '@tiptap/vue-3'
import { StarterKit } from '@tiptap/starter-kit'

export default {
  components: {
    EditorContent,
  },
  data () {
    return {
      editor: null,
      content: null,
      toolbar: [
          {
              icon: 'material-symbols:format-bold',
              callback: () => {
                  this.editor.chain().focus().toggleBold().run()
              }
          },
          {
              icon: 'material-symbols:format-italic',
              callback: () => {
                  this.editor.chain().focus().toggleItalic().run()
              }
          },
          {
              icon: 'material-symbols:format-list-bulleted',
              callback: () => {
                  this.editor.chain().focus().toggleBulletList().run()
              }
          },
          {
              icon: 'material-symbols:format-list-numbered',
              callback: () => {
                  this.editor.chain().focus().toggleOrderedList().run()
              }
          }
      ]
    }
  },
  mounted () {
    this.editor = new Editor({
      content: null,
      extensions: [
        StarterKit,
      ],
      editorProps: {
          attributes: {
              class: 'prose prose-sm sm:prose prose-rose lg:prose-lg xl:prose-2xl mx-auto focus:outline-none min-h-96 h-96 p-4',
          },
      },
      onUpdate: ({ editor }) => {
          this.content = JSON.stringify(editor.getJSON(), null, 2)
      }
    })
  },
  beforeUnmount() {
    this.editor.destroy()
  }
}
</script>
