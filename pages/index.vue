<template>
  <div>
    <ul>
      <li>{{ $ua.deviceType() }}</li>
      <li>{{ $ua.os() }}</li>
      <li>{{ $ua.osVersion() }}</li>
      <li>{{ $ua.browser() }}</li>
      <li>{{ $ua.browserVersion() }}</li>
      <li>{{ $ua.browserVendor() }}</li>
      <li>{{ $ua.isFromIphone() ? 'iPhone' : 'not iPhone' }}</li>
      <li>{{ $ua.isFromIpad() ? 'iPad' : 'not iPad' }}</li>
      <li>{{ $ua.isFromIpod() ? 'iPod' : 'not iPod' }}</li>
      <li>{{ $ua.isFromIos() ? 'iOS' : 'not iOS' }}</li>
      <li>{{ $ua.isFromAndroidOs() ? 'Android OS' : 'not Android OS' }}</li>
      <li>{{ $ua.isFromAppliance() ? 'Appliance' : 'not Appliance' }}</li>
      <li>{{ userAgent }}</li>
    </ul>
    <hr />
    <ul>
      <li v-for="(device, index) in devices" :key="index">
        {{ device.deviceId }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userAgent: '',
      devices: []
    }
  },
  async mounted() {
    if (process.browser) {
      this.userAgent = window.navigator.userAgent
      this.devices = await window.navigator.mediaDevices.enumerateDevices()
      console.log(this.devices)
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
