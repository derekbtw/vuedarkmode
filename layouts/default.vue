<!-- *************************************************************************
     TEMPLATE
     ************************************************************************* -->

<template lang="pug">
.l-default
  .l-default__container
    the-navigation(
      @titleClick="onNavigationClick"
      @itemClick="onNavigationClick"
      :categories="navigation.categories"
      class="l-default__navigation"
    )
    .l-default__page-wrapper
      the-github-corner(
        link="https://github.com/LeCoupa/vuedarkmode"
        class="l-default__github-corner"
      )
      .l-default__page-inner
        nuxt
</template>

<!-- *************************************************************************
     SCRIPT
     ************************************************************************* -->

<script>
// PROJECT
import TheGithubCorner from "@/components/layouts/TheGithubCorner";
import TheNavigation from "@/components/layouts/TheNavigation";

export default {
  components: {
    TheGithubCorner,
    TheNavigation
  },

  data() {
    return {
      // --> COMPONENTS <--

      navigation: {
        categories: [
          {
            id: "installation",
            title: "💻 Installation"
          },
          {
            id: "packageOptions",
            title: "📦 Package Options"
          },
          {
            id: "colors",
            title: "🎨 Colors"
          },
          {
            id: "base",
            title: "🤖 Base Components",
            items: [
              {
                label: "Alerts",
                id: "baseAlert"
              },
              {
                label: "Avatars",
                id: "baseAvatar"
              },
              {
                label: "Badges",
                id: "baseBadge"
              },
              {
                label: "Buttons",
                id: "baseButton"
              },
              {
                label: "Dividers",
                id: "baseDivider"
              },
              {
                label: "Headings",
                id: "baseHeading"
              },
              {
                label: "Icons",
                id: "baseIcon"
              },
              {
                label: "List Items",
                id: "baseListItem"
              },
              {
                label: "Progress Bars",
                id: "baseProgressBar"
              },
              {
                label: "Social Logins",
                id: "baseSocialLogin"
              },
              {
                label: "Spinners",
                id: "baseSpinner"
              },
              {
                label: "Toasts",
                id: "baseToast"
              }
            ]
          },
          {
            id: "form",
            title: "📃 Form Components",
            items: [
              {
                label: "Checkboxes",
                id: "fieldCheckbox"
              },
              {
                label: "Files",
                id: "fieldFile"
              },
              {
                label: "Inputs",
                id: "fieldInput"
              },
              {
                label: "Radios",
                id: "fieldRadio"
              },
              {
                label: "Selects",
                id: "fieldSelect"
              },
              {
                label: "Tabs",
                id: "fieldTabs"
              },
              {
                label: "Textareas",
                id: "fieldTextarea"
              },
              {
                label: "Toggles",
                id: "fieldToggle"
              }
            ]
          }
        ]
      }
    };
  },

  mounted() {
    let hash = this.$route.hash;

    if (hash) {
      this.scrollToSection(hash.substr(1));
    }
  },

  methods: {
    // --> EVENT LISTENERS <--

    onNavigationClick(id) {
      this.scrollToSection(id);
    },

    // --> HELPERS <--

    scrollToSection(id) {
      const section = this.$el.querySelector(`#${id}`);

      if (section) {
        section.scrollIntoView({
          behavior: "smooth",
          block: "start",
          inline: "nearest"
        });
      }
    }
  }
};
</script>

<!-- *************************************************************************
     STYLE
     ************************************************************************* -->

<style lang="scss">
// Imported stylesheets for Javascript libraries (e.g. nprogress)
@import "assets/libraries/libraries.animate";
@import "assets/libraries/libraries.highlightjs";

// Unclassed HTML elements (e.g. a {}, blockquote {}, address {})
@import "./assets/elements/elements.inline";

// Objects, abstractions, and design patterns (e.g. .o-flexbox-column {})
@import "./assets/objects/objects.layouts";

// High-specificity, very explicit selectors
@import "./assets/utilities/utilities.alignments";
@import "./assets/utilities/utilities.inline";

// VARIABLES
$c: ".l-default";

html {
  background-color: $mirage;
  color: $white;
  text-align: center;
  word-spacing: 1px;
  font-size: 16px;
  font-family: "Heebo", "Helvetica Neue", Source Sans Pro, Helvetica, Arial,
    sans-serif;

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  -webkit-text-size-adjust: 100%;
  -ms-text-size-adjust: 100%;

  a {
    outline: 0;
    text-decoration: none;
    cursor: pointer;

    &:focus {
      box-shadow: 0 2px 0 $azure-radiance;
      transition: box-shadow ease-in-out 0s;
    }
  }

  #{$c} {
    #{$c}__container {
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      display: flex;
      overflow: hidden;

      #{$c}__navigation {
        flex: 0 0 auto;
      }

      #{$c}__page-wrapper {
        position: relative;
        overflow-y: scroll;
        flex: 1;
        padding: 60px 40px;

        #{$c}__github-corner {
          position: absolute;
          top: 0;
          right: 0;
          border: 0;
        }

        #{$c}__page-inner {
          margin: 0 auto;
          max-width: 900px;
        }
      }
    }
  }
}
</style>
