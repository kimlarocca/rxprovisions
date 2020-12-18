<template>
  <div class="l-container">
    <v-spacer />
    <v-header
        layout="right"
        :responsive=true
    >
      <template v-slot:logo>
        <img
            src="/images/logo.jpg"
            width="150"
            alt="GeneLeap Bioteach logo"
        />
      </template>
      <template v-slot:button>
        <v-button href="http://www.google.com">
          Investors
        </v-button>
      </template>
      <template v-slot:menu>
        <v-menu
            layout="right"
            :primaryNav="[
                    {
                      url: '/about',
                      text: 'About',
                    },
                    {
                      url: '/technology',
                      text: 'Technology',
                    },
                    {
                      url: '/careers',
                      text: 'Careers',
                    },
                    {
                      url: '/news',
                      text: 'News',
                    },
                    {
                      url: '/contact',
                      text: 'Contact',
                    }
                  ]"
        >
          <template v-slot:logo>
            <img
                src="https://place-hold.it/150x50?text=logo"
                alt="logo"
            />
          </template>
          <template v-slot:button>
            <v-button href="http://www.google.com">
              Click Me
            </v-button>
          </template>
          <template v-slot:component>
            <p class="u-align--center"><em>slot for component</em></p>
          </template>
          <template v-slot:social>
            <ul class="social-links">
              <social-link
                  icon="fab fa-facebook-f"
                  link="https://www.facebook.com"
                  label="facebook"
              >
              </social-link>
              <social-link
                  icon="fab fa-twitter"
                  link="https://www.twitter.com"
                  label="twitter"
              >
              </social-link>
              <social-link
                  icon="fab fa-youtube"
                  link="https://www.youtube.com"
                  label="youtube"
              >
              </social-link>
              <social-link
                  icon="fab fa-instagram"
                  link="https://www.instagram.com"
                  label="instagram"
              >
              </social-link>
              <social-link
                  icon="fab fa-linkedin-in"
                  link="https://www.linkedin.com"
                  label="linkedin"
              >
              </social-link>
            </ul>
          </template>
        </v-menu>
      </template>
      <template v-slot:navigation>
        <secondary-navigation
            orientation="horizontal"
            :nav-items="[
                    {
                      url: '/about',
                      text: 'About',
                    },
                    {
                      url: '/technology',
                      text: 'Technology',
                    },
                    {
                      url: '/careers',
                      text: 'Careers',
                    },
                    {
                      url: '/news',
                      text: 'News',
                    },
                    {
                      url: '/contact',
                      text: 'Contact',
                    }
                  ]"
        />
      </template>
    </v-header>
    <v-spacer size="hex" />
    <router-view />
    <v-spacer size="hex" />
  </div>
  <v-footer
      company-name="GeneLeap Biotech"
      :navigation="[
                    {
                      url: '/about',
                      text: 'About',
                    },
                    {
                      url: '/technology',
                      text: 'Technology',
                    },
                    {
                      url: '/careers',
                      text: 'Careers',
                    },
                    {
                      url: '/news',
                      text: 'News',
                    },
                    {
                      url: '/contact',
                      text: 'Contact',
                    },
                    {
                      url: '/privacy',
                      text: 'Privacy',
                    },
                    {
                      url: '/terms',
                      text: 'Terms',
                    }
                  ]"
  >
    <template v-slot:blurb>
      <p>Unless otherwise specified, all product names appearing on this Internet site are trademarks owned by or licensed to Luye Boston R&D IIC, its subsidiaries or affiliates. No use of any Luye Boston R&D IIC trademark, trade name, or trade dress on this site may be made without the prior written authorization of Luye Boston R&D IIC except to identify the product or services of the company. This Luye Boston R&D IIC website focusing on science is intended for the use of U.S. healthcare professionals any sciences.</p>
    </template>
  </v-footer>
</template>

<script>
import SecondaryNavigation from 'vue-evolve/src/components/SecondaryNavigation'
import SocialLink from 'vue-evolve/src/components/SocialLink'
import VButton from 'vue-evolve/src/components/VButton'
import VHeader from 'vue-evolve/src/components/VHeader'
import VMenu from 'vue-evolve/src/components/VMenu'
import VSpacer from 'vue-evolve/src/components/VSpacer'
import VFooter from 'vue-evolve/src/components/VFooter'

export default {
  name: 'GeneLeap',
  components: {
    SecondaryNavigation,
    SocialLink,
    VButton,
    VHeader,
    VMenu,
    VSpacer,
    VFooter
  }
}
</script>
