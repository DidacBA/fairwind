<template>
  <div class="page-content grid md:grid-flow-col grid-flow-row">
    <div class="contact-content-wrapper mx-auto px-6">
      <div class="sm:w-full sm:px-8 flex flex-col md:flex-row justify-between">
        <div class="flex flex-col text-gray-800 md:p-6">
          <span class="font-bold uppercase">Phone</span>
          <span class="my-2"><a :href="`tel:${contact.phone}`" class="text-md hover:text-blue-500" rel="noreferrer">{{ contact.phone }}</a></span>
          <span class="font-bold uppercase">E-mail</span>
          <span class="my-2">
            <a :href="`mailto:${contact.email}`" class="text-md hover:text-blue-500" rel="noreferrer">
              {{ contact.email }}
            </a>
          </span>
          <span class="font-bold uppercase">Follow Us</span>
          <div class="social-media-links text-4xl">
            <a :href="contact.facebook" target="_blank" rel="noreferrer">
              <span class="sr-only">Link to Facebook</span>
              <font-awesome-icon :icon="{ prefix: 'fab', iconName: 'facebook' }" />
            </a>
            <a :href="contact.instagram" target="_blank" rel="noreferrer">
              <span class="sr-only">Link to Instagram</span>
              <font-awesome-icon :icon="{ prefix: 'fab', iconName: 'instagram' } "/>
            </a>
          </div>
        </div>
        <div class="flex flex-col md:flex-row p-4">
          <div class="font-light text-gray-800 text-md p-4 flex flex-col align-center">
            <p class="mt-3 text-center md:text-left">Edgewater Marina</p>
            <p class="mt-2 text-center md:text-left">989 River Rd</p>
            <p class="mt-2 text-center md:text-left">Edgewater NJ, 07020</p>
          </div>
          <div class="w-full md:w-1/2">
            <iframe title="fairwind-charters-map" width="100%" frameborder="0" scrolling="no" marginheight="0" marginwidth="0" src="https://maps.google.com/maps?width=100%25&amp;height=600&amp;hl=en&amp;q=Fairwind%20Charters%20Edgewater%20Marina+(Fairwind%20Charters)&amp;t=&amp;z=14&amp;ie=UTF8&amp;iwloc=B&amp;output=embed"></iframe>
          </div>
        </div>
      </div>
      <form class="w-full md:p-6" name="contactus" method="post" data-netlify="true" netlify-honeypot="bot-field" data-netlify-recaptcha="true">
        <input type="hidden" name="form-name" value="contactus" />
        <div class="flex flex-wrap -mx-3 mb-6">
          <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
            <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
              First Name
            </label>
            <input v-model="name" :class="[ nameError ? 'border-red-500' : 'border-gray-200' ]" class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="grid-first-name" type="text" name="firstname" placeholder="Jane">
            <p :class="[ nameError ? 'block' : 'hidden' ]" class="text-red-500 text-xs italic hidden">Please fill out this field.</p>
          </div>
          <div class="w-full md:w-1/2 px-3">
            <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-last-name">
              Last Name
            </label>
            <input v-model="lastname" :class="[ lastnameError ? 'border-red-500' : 'border-gray-200' ]"  class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500" id="grid-last-name" name="lastname" type="text" placeholder="Doe">
            <p :class="[ lastnameError ? 'block' : 'hidden' ]" class="text-red-500 text-xs italic hidden">Please fill out this field.</p>
          </div>
        </div>
        <div class="flex flex-wrap -mx-3 mb-6">
          <div class="w-full md:w-1/2 px-3">
            <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-email">
              E-mail
            </label>
            <input v-model="email" :class="[ emailError ? 'border-red-500' : 'border-gray-200' ]"  class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500" id="email" name="email" type="email">
            <p :class="[ emailError ? 'block' : 'hidden' ]" class="text-red-500 text-xs italic">Please fill out this field</p>
          </div>
          <div class="w-full md:w-1/2 px-3">
            <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-phone">
              Phone number
            </label>
            <input v-model="phone" :class="[ lastnameError ? 'border-red-500' : 'border-gray-200' ]"  class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500" id="phone" name="phone" type="tel" placeholder="000-000-0000">
            <p :class="[ lastnameError ? 'block' : 'hidden' ]" class="text-red-500 text-xs italic hidden">Please fill out this field.</p>
          </div>
        </div>
        <div class="flex flex-wrap -mx-3 mb-6">
          <div class="w-full px-3">
            <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-message">
              Message
            </label>
            <textarea v-model="msg" :class="[ msgError ? 'border-red-500' : 'border-gray-200' ]"  class="no-resize appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500 h-48 resize-none" id="message" name="message"></textarea>
            <p :class="[ msgError ? 'block' : 'hidden' ]" class="text-red-500 text-xs italic">Please fill out this field</p>
          </div>
        </div>
        <div data-netlify-recaptcha="true"></div>
        <div class="md:flex md:items-center">
          <div class="md:w-1/3">
            <button @click="validate" class="shadow bg-fairwind-pink-100 hover:bg-fairwind-pink-200 focus:shadow-outline focus:outline-none text-white font-bold py-2 px-4 rounded" type="submit" value="Send message">
              Send
            </button>
          </div>
          <div class="md:w-2/3"></div>
        </div>
      </form>
    </div>
    <div class="mx-auto md:flex md:flex-col md:items-end md:h-screen md:w-full md:sticky inset-y-0 row-start-1 md:row-auto">
      <h1 class="section-title font-page-title md:relative m-0 md:transform md:rotate-270 text-fairwind-medium-blue text-6xl whitespace-no-wrap">Contact Us</h1>
    </div>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: 'Fairwind Charters: Contact Us',
    }
  },
  computed: {
    content() {
      return this.$store.state.siteContent.faqs
    },
    contact() {
      return this.$store.state.siteContent.contactus
    }
  },
  data() {
    return {
      name: '',
      lastname: '',
      phone: '',
      email: '',
      msg: '',
      nameError: false,
      lastnameError: false,
      emailError: false,
      msgError: false,
    }
  }
}
</script>

<style lang="postcss" scoped>
.section-title {
  @media (min-width: 768px) {
    font-size: 10vw;
    width: 10vw;
    top: 4.25em;
  }
  @media (min-width: 1600px) {
    font-size: 160px;
  }
}
.contact-content-wrapper {
  width: 90vw;
}
</style>
