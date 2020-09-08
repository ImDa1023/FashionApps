<template>
  <v-ons-page>
    <v-ons-toolbar>
      <div class="center">{{ title }}</div>
    </v-ons-toolbar>

    <v-ons-tabbar position="auto"
      :tabs="tabs"
      :visible="true"
      :index.sync="activeIndex"
    >
    </v-ons-tabbar>
  </v-ons-page>
</template>

<script>
  import myPage from 'Mypage';
  import homePage from 'Home';
  import questionPage from 'Question';
  import savePage from 'Save';

  export default {
    data() {
      return {
        activeIndex: 0,
        tabs: [
	  {
	    icon: this.md() ? null : 'ion-home',
	    label: 'Home',
	    page: homePage
	  },
    {
	    icon: this.md() ? null : 'ion-ios-help-outline',
	    label: 'Question',
	    page: questionPage
	  },
	  {
	    icon: this.md() ? null : 'ion-ios-cloud',
	    label: 'Save',
	    page: savePage
	  },
    {
	    icon: this.md() ? null : 'ion-ios-person',
	    label: 'Mypage',
	    page: myPage,
	  },
        ]
      };
    },
    methods: {
      md() {
        return this.$ons.platform.isAndroid();
      }
    },
    computed: {
      title() {
        return this.tabs[this.activeIndex].label;
      }
    },
    components: { homePage, myPage, savePage, questionPage }
  }
</script>