<template>
  <div id="terminal">
    <span id="line-0">&gt; <span id="text">{{ text }}</span><span id="cursor">_</span></span>
  </div>
</template>

<script>
export default {
  props: {

  },
  data() {
    return {
      text: ''
    };
  },
  mounted() {
    // bindings
    
    // globals
    this._delay = 120;
    this._step = 0;
    this._message = 0;
    this._messages = [
      'seek and deploy',
      'envision a future free from their control',
      'v1.0 initializing 9.1.2025'
    ];
    this._letters = this._messages.map((el) => el.split(''));

    this.go();
  },
  methods: {
    go() {
      this.text = this._letters[this._message].slice(0, this._step).join('');

      if(this._step <= this._letters[this._message].length) {
        this._delay = 120;
        this._step += 1;
      } else {
        this._step = 0;
        this._delay = 2000;

        if(this._message < this._messages.length - 1) this._message += 1;
        else this._message = 0;
      }

      setTimeout(() => {
        this.go();
      }, this._delay);
    }
  }
};
</script>

<style lang="scss">
#terminal {
  position: relative;
  height: 100%;

  #line-0 {
    position: absolute;
    top: 50%;
    left: 50%;
    color: #878f87;
    font-weight: bold;
    transform: translate(-50%, -50%);

    #cursor {
      animation: cursor 1s step-start 0s infinite;
    }
  }
}

@keyframes cursor {
  50% {
    opacity: 0;
  }
}
</style>