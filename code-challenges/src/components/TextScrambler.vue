<template>
  <div class="main">
    <div class="item">
      <textarea 
        placeholder="Add text"
        v-model="message"
      >
        Text
      </textarea>
      <div
        class="main-error"
        v-if="error">
        <p>Type something</p>
      </div>
    </div>
    <div class="item">
      <button
        class="show-text"
        v-on:click="showText"
      >
        {{ changeTextButton }}
      </button>
    </div>
    <div class="item">
      <textarea
        readonly="readonly"
        class="scrambled-text"
        :class="{show: showHideText}"
        v-model="scrambledText"
      >
      </textarea>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TextScrambler',
  data() {
   return {
     message: '',
     showHideText: false,
     error: false
   }
  },
  computed: {
    scrambledText: function () {
      return this.message.split('').sort(() => Math.random() - 0.5).join('');
    },
    changeTextButton: function () {
      return !this.showHideText ? 'Show Message' : 'Hide Message'
    }
  },
  methods: {
    showText: function () {
      if (this.message === '' && this.showHideText === true) {
        this.showHideText = false;
        this.error = true;
      }
      else if (!this.message) {
        this.error = true;
      }
      else {
        this.error = false;
        this.showHideText = !this.showHideText;
      }
    }
  }
}
</script>

<style lang="scss" scoped>

@mixin box-shadow {
  box-shadow: 2px 4px 4px rgb(0 0 0 / 20%);
}

.main {
  display: flex;
  flex-direction: column;
  width: 400px;

  .item {
    position: relative;
  }

  p,
  textarea,
  button {
    display: block;
    font-size: 16px;
    font-family: inherit;
    text-align: center;
  }
}

.show-text {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
  border-radius: 0 0 10px 10px;
  transition: background-color .3s, color .3s;
  background-color: burlywood;
  color: brown;
  @include box-shadow;

  &:hover {
    background-color: cadetblue;
    color: gainsboro;
  }
}

textarea {
  width: 100%;
  padding: 10px 5px;
  border-radius: 10px 10px 0 0;
  @include box-shadow;
}

.scrambled-text {
  white-space: pre-line;
  background-color: rgb(255, 255, 255);
  padding: 10px 5px;
  width: 100%;
  min-height: 70px;
  transition: opacity .3s;
  opacity: 0;
  border-radius: 10px;
  margin-top: 10px;
  @include box-shadow;

  &.show {
    opacity: 1;
  }
}

.main-error {
  background-color: chocolate;
  color: antiquewhite;
  width: 210px;
  height: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50px 10px 50px 0;
  position: absolute;
  transform: translate(180px, -30px);
  top: 0;
  right: 0;
  pointer-events: none;
  @include box-shadow;
}

</style>
