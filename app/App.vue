<template>
  <Page>
    <ActionBar title="#JavaScript30 - Clock_02"/>
    <TabView>
      <TabViewItem title="Show me the Clock!">
        <StackLayout>
          <Label class="clock" :text="`${hours}:${minutes}:${seconds} ${meridiem}`" backgroundColor="#000000"/>
          <Label class="description" text="For this project, I used JavaScript Date methods with Vue's reactivity system to display the current time down to the second." textWrap="true"/>
          <Label class="footer" text="This mobile application was built using Vue-NativeScript!" textWrap="true"/>
          <Image class="vns-logo" src="~/assets/images/ns-vue.png" stretch="none"/>
        </StackLayout>
      </TabViewItem>
      <TabViewItem title="About Me">
        <StackLayout class="bio">
        <WebView src="~/assets/clock.html"/>
        </StackLayout>
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
    background-color: #2b2d2e;
    color: #ffffff;
  }

  Label.clock {
    margin: 24;
    color: #08ff00;
    font-weight: bold;
    font-family: monospace;
    padding: 12;
    text-align: center;
    font-size: 48;
    border-radius: 25px;
  }

  Label.description {
    padding: 24;
    font-size: 22;
    text-align: center;
    border-bottom: 1px solid #ccc;
  }

  Label.footer {
    padding: 24;
    padding-bottom: 0;
    font-size: 22;
    text-align: center;
  }

  Image.vns-logo {
    padding: 48;
    margin: 24;
  }

  .bio {
    padding: 12;
  }

</style>
