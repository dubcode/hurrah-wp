<template>
  <ul class="flex justify-left items-center h-full">
    <li v-for="icon in icon_links" :key="icon.id" class="flex justify-center items-center h-full mr-2 md:mr-6">
      <a :href="icon.link" class="block" target="_blank" v-html="icon.vector" />
    </li>
  </ul>
</template>

<script>
export default {
  data () {
    return {
      icon_links: [
        {
          id: '1',
          link: 'https://www.facebook.com/Hurrah-Marketing-101699818175153/',
          vector:
            '<svg class="fill-current text-pink hover:text-grey" width="20px" height="20px" viewBox="0 0 320 512"><path d="M279.14 288l14.22-92.66h-88.91v-60.13c0-25.35 12.42-50.06 52.24-50.06h40.42V6.26S260.43 0 225.36 0c-73.22 0-121.08 44.38-121.08 124.72v70.62H22.89V288h81.39v224h100.17V288z"></path></svg>'
        },
        {
          id: '2',
          link: 'https://www.linkedin.com/company/hurrahmarketing/',
          vector:
            '<svg class="fill-current text-pink hover:text-grey" width="20px" height="20px" viewBox="0 0 448 512"><path d="M100.28 448H7.4V148.9h92.88zM53.79 108.1C24.09 108.1 0 83.5 0 53.8a53.79 53.79 0 0 1 107.58 0c0 29.7-24.1 54.3-53.79 54.3zM447.9 448h-92.68V302.4c0-34.7-.7-79.2-48.29-79.2-48.29 0-55.69 37.7-55.69 76.7V448h-92.78V148.9h89.08v40.8h1.3c12.4-23.5 42.69-48.3 87.88-48.3 94 0 111.28 61.9 111.28 142.3V448z"></path></svg>'
        },
        {
          id: '3',
          link: 'mailto:hello@hurrahmarketing.co.uk',
          vector:
            '<svg class="fill-current text-pink hover:text-grey" width="20px" height="20px" viewBox="0 0 512 512"><path d="M502.3 190.8c3.9-3.1 9.7-.2 9.7 4.7V400c0 26.5-21.5 48-48 48H48c-26.5 0-48-21.5-48-48V195.6c0-5 5.7-7.8 9.7-4.7 22.4 17.4 52.1 39.5 154.1 113.6 21.1 15.4 56.7 47.8 92.2 47.6 35.7.3 72-32.8 92.3-47.6 102-74.1 131.6-96.3 154-113.7zM256 320c23.2.4 56.6-29.2 73.4-41.4 132.7-96.3 142.8-104.7 173.4-128.7 5.8-4.5 9.2-11.5 9.2-18.9v-19c0-26.5-21.5-48-48-48H48C21.5 64 0 85.5 0 112v19c0 7.4 3.4 14.3 9.2 18.9 30.6 23.9 40.7 32.4 173.4 128.7 16.8 12.2 50.2 41.8 73.4 41.4z"></path></svg>'
        },
        {
          id: '4',
          link: 'tel:07814932345',
          vector:
            '<svg class="fill-current text-pink hover:text-grey" width="20px" height="20px" viewBox="0 0 320 512"><path d="M272 0H48C21.5 0 0 21.5 0 48v416c0 26.5 21.5 48 48 48h224c26.5 0 48-21.5 48-48V48c0-26.5-21.5-48-48-48zM160 480c-17.7 0-32-14.3-32-32s14.3-32 32-32 32 14.3 32 32-14.3 32-32 32zm112-108c0 6.6-5.4 12-12 12H60c-6.6 0-12-5.4-12-12V60c0-6.6 5.4-12 12-12h200c6.6 0 12 5.4 12 12v312z"></path></svg>'
        }
      ]
    }
  }
}
</script>
