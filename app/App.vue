<template>
  <Page>
    <ActionBar title="Vue-NativeScript Clock"/>
    <TabView>
      <TabViewItem title="Show me the Clock!">
        <StackLayout>
          <Label class="clock" :text="`${hours}:${minutes}:${seconds} ${meridiem}`"/>
        </StackLayout>
      </TabViewItem>
      <TabViewItem title="About Me">
        <WebView class="bio" src="~/assets/clock.html"/>
      </TabViewItem>
    </TabView>

  </Page>
</template>

<script>
  export default {
    data() {
      return {
        msg: 'Hello World!',
        now: new Date
      }
    },
    computed: {
      hours() {
        let h = this.now.getHours();
        if(h === 0) h = 12;

        if(h > 12) h = h - 12;

        return (h < 10) ? "0" + h : h;
      },
      minutes() {
        let m = this.now.getMinutes();
        return (m < 10) ? `0${m}` : m;
      },
      seconds() {
        let s = this.now.getSeconds();
        return (s < 10) ? `0${s}` : s;
      },
      meridiem() {
        const h = this.now.getHours();
        return (h > 12) ? 'PM' : 'AM'
      }
    },
    created() {
      setInterval(() => this.now = new Date, 1);
    }
  }
</script>

<style scoped>
  ActionBar {
    background-color: #53ba82;
    color: #ffffff;
  }

  Label {
    padding: 25;
    font-size: 64;
  }


  .bio {
    padding: 25;
  }


</style>
