<template>
  <div class="navbar">
    <v-row no-gutters justify="center" align="center">
      <v-col cols="12" lg="2" md="2" sm="12">
        <div class="navbar-logo">
          <img
            src="https://images.squarespace-cdn.com/content/v1/594eb9274c8b03ee09b041e9/1528591440366-78RJBR8X2SVTHVFLZVWK/download.gif?format=1500w"
            width="75px"
          />
        </div>
      </v-col>
      <v-col cols="10" v-if="!$vuetify.breakpoint.smAndDown">
        <div class="navbar-list">
          <div class="center">
            <ul v-for="nav in navbar" :key="nav">
              <li style="padding: 0 15px;">{{ nav.name }}</li>
            </ul>
          </div>
          <div class="center">
            <ul v-for="social in socials" :key="social">
              <li :class="social.color" class="center">
                <i :class="social.icon" style="font-size: 20px;"></i>
              </li>
            </ul>
          </div>
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      navbar: [
        { name: 'Home', link: '#', icon: '', iconAlt: 'Home Page' },
        { name: 'About', link: '#', icon: '', iconAlt: 'About Page' },
        { name: 'Skills', link: '#', icon: '', iconAlt: 'Skills Page' },
        { name: 'Projects', link: '#', icon: '', iconAlt: 'Project Page' },
        { name: 'Blogs', link: '#', icon: '', iconAlt: 'Blogs Page' },
        { name: 'Contact', link: '#', icon: '', iconAlt: 'Contact Page' },
      ],
      socials: [
        {
          link: '#',
          icon: 'fab fa-facebook',
          iconAlt: 'facebook',
          color: "facebook"
        },
        {
          link: '#',
          icon: 'fab fa-twitter',
          iconAlt: 'twitter',
          color: "twitter"
        },
        {
          link: '#',
          icon: 'fab fa-linkedin',
          iconAlt: 'linkedin',
          color: "linkedin"
        },
        {
          link: '#',
          icon: 'fab fa-pinterest',
          iconAlt: 'pinterest',
          color: "pinterest"
        },
        {
          link: '#',
          icon: 'far fa-envelope',
          iconAlt: 'gmail',
          color: "gmail"
        }
      ],
    }
  },
}
</script>

<style>
.navbar-list {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.navbar-logo {
  display: flex;
  justify-content: center;
  align-items: center;
}

.navbar-list ul li {
  padding: 0 5px;
  list-style: none;
  font-size: 17px;
  font-family: var(--navbar-font);
}
</style>