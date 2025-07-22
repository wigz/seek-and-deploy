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
      '',
      'matt@seekanddeploy.com'
    ];
    this._quotes = [
      "we fight for the user",
      "setec astronomy ... too many secrets",
      "follow the white rabbit",
      "don't solve with more, solve with less",
      "spot, you are disrupting my ability to work"
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
        this._letters[1] = this._quotes[Math.floor(Math.random() * this._quotes.length)].split('');

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
  padding: 20px;

  #line-0 {
    color: #828582;
    font-weight: bold;

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