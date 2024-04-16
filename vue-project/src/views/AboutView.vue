<template>
  <div class="wrap">
    <div class="container">
      <div class="left">
        <div class="title">SEND <br> A REQUEST</div>
        <div class="description">
          Leave your contacts <br>
          and we will contact <br>
          you as soon as possible</div>
        <div class="logo"><img src="../assets/l.svg" alt=""></div>
      </div>
      <div class="right">
        <form novalidate @submit.prevent="myMethod">
          <div class="wrapper_inputs">
            <div :class='{ invalid: invalid }' class="field tel-field mr-2">
              <div class="input-field inputBox">
                <input v-model="inputValue" type="phone" class="tel" pattern="" />
                <span>PHONE</span>
              </div>
              <span class="error tel-error">
                <i class="bx bx-error-circle error-icon"></i>
                <p class="error-text">Формат телефона +7 (777) 777-77-77</p>
              </span>
            </div>
            <div class="field text-field mr-2">
              <div class="input-field inputBox">
                <input type="text" class="name" />
                <span>NAME</span>
              </div>
            </div>
            <div class="field comments-field mr-2">
              <div class="input-field inputBox">
                <input type="text" class="comments" />
                <span>COMMENTS</span>
              </div>
            </div>
            <div class="field range">
              <div class="rangeText">TEMP</div>
              <input type="range">
            </div>


          </div>
          <div class="field create-call">
            <div class="field button-field input-field">
              <input type="submit" value="CALL ME" />
              <div class="text">By pressing “Send” button <br>
                I agree with <span class="colorText">Privacy Policy</span></div>
            </div>
          </div>
        </form>
      </div>
    </div>
    <footer>
      <ul>
        <li class="copytight">&copy; 2022 LUXURY RESIDENCE</li>
        <li>Privacy Policy</li>
      </ul>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputValue: '',
      telPattern: /^\+7\s?\(\d{3}\)\s?\d{3}-?\d{2}-?\d{2}$/,
      invalid: false
    }
  },
  methods: {
    myMethod(e) {
      e.preventDefault();
      if (!this.inputValue.match(this.telPattern)) {
        this.invalid = true
      } else {
        console.log('валидация прошла')
        this.invalid = false
      }

    }
  },
}
</script>

<style scoped lang="scss">
$overall_color: #EEEBE6;
$color_2: #919191;
$color_3: #d93025;
$color_4: #fff;
$color_pink: #FF69B4;

@font-face {
  font-family: 'GHAEm';
  src: url('../assets/font/GHEA/gheamariam.otf');
}

@font-face {
  font-family: 'GHAE';
  src: url('../assets/font/GHEA/gheagrapalat.otf');
}

@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}

@media screen and (-webkit-min-device-pixel-ratio:0) {
  input[type='range'] {
    overflow: hidden;
    width: 100%;
    -webkit-appearance: none;
    background-color: #5BAAF9;
  }

  input[type='range']::-webkit-slider-runnable-track {
    height: 3px;
    // -webkit-appearance: none;
    color: #13bba4;
    margin-top: -1px;
  }

  input[type='range']::-webkit-slider-thumb {
    width: 10px;
    -webkit-appearance: none;
    height: 50px;
    cursor: ew-resize;
    background: #fff;
    box-shadow: -1000px 0 0 1000px #FF69B4;
    position: relative;
  }


}

.rangeText {
  font-size: 16px;
  color: #EEEBE6;
  margin-top: 10px;
}

/** FF*/
input[type="range"]::-moz-range-progress {
  background-color: #FF69B4;
}

input[type="range"]::-moz-range-track {
  background-color: #5BAAF9;
}

/* IE*/
input[type="range"]::-ms-fill-lower {
  background-color: #FF69B4;
}

input[type="range"]::-ms-fill-upper {
  background-color: #5BAAF9;
}



*::-webkit-input-placeholder {
  color: $overall_color;
}

*:-moz-placeholder {
  color: $overall_color;
  opacity: 1;
}

*::-moz-placeholder {
  color: $overall_color;
  opacity: 1;
}

*:-ms-input-placeholder {
  color: $overall_color;
}

*::-ms-input-placeholder {
  color: $overall_color;
}

*::placeholder {
  color: $overall_color;
}

.wrap {
  background: #21354B;
  color: #EEEBE6;
  padding: 56px 86px;
  font-family: 'GHAE';
  text-transform: uppercase;

  footer {
    ul {
      list-style-type: none;
      padding: 0;
      display: flex;
      margin: 90px 0;

      li {
        font-size: 12px;
        margin-right: 208px;

        &.copytight {
          color: $color_pink;
        }
      }
    }
  }

  .container {
    position: relative;
    width: 100%;
    border-radius: 8px;
    display: flex;
    justify-content: space-between;

    .left,
    .right {
      width: 100%;
    }

    .left {
      .title {
        font-size: 66px;
        font-family: 'GHAEm';
        line-height: 72px;
        margin-bottom: 90px;
      }

      .description {
        font-size: 14px;
        margin-bottom: 97px;
      }
    }

    form {
      margin-top: 180px;
    }
  }
}

form {
  max-width: 536px;

  .field {
    margin-bottom: 20px;
    flex-grow: 1;

    &.range {
      position: relative;

      &::after {
        content: 'HOT';
        position: absolute;
        bottom: -17px;
        left: 0;
        font-size: 9px;
      }

      &::before {
        content: 'COLD';
        position: absolute;
        bottom: -17px;
        right: 0;
        font-size: 9px;
      }

    }
  }

  .input-field {
    position: relative;
    width: 100%;
    height: 55px;
  }

  .wrapper_inputs {
    display: flex;
    flex-direction: column;
  }
}

.input-field {
  input {
    width: 100%;
    height: 100%;
    padding: 0;
    border: none;
    border-bottom: 1px solid $overall_color;
    outline: none;
    background: none;
    color: $overall_color;
  }

  .password-hide {
    position: absolute;
    top: 50%;
    right: 15px;
    transform: translateY(-50%);
    font-size: 18px;
    color: $color_2;
    padding: 3px;
    cursor: pointer;
  }
}

.invalid {
  input {
    border-bottom: 1px solid #d93025;
  }

  .error {
    display: flex !important;
  }
}

.field {
  .error {
    align-items: center;
    margin-top: 6px;
    font-size: 14px;
    font-weight: 400;
    color: $color_3;
    display: none;
  }
}

.error {
  .error-icon {
    font-size: 15px;
    margin-right: 6px;
  }

  .error-text {
    font-size: 12px;
  }
}

.create-call {
  .error {
    align-items: flex-start;
  }

  .error-icon {
    margin-top: 4px;
  }
}

.button-field {
  margin: 136px 0 0px 0px;
  display: flex;
  align-items: center;

  .text {
    font-size: 13px;

    .colorText {
      color: $color_pink;
    }
  }

  input {
    font-size: 16px;
    font-weight: 400;
    color: #EEEBE6;
    transition: all 0.3s;
    cursor: pointer;
    width: 173px;
    height: 56px;
    border: 1px solid #EEEBE6;
    border-radius: 100px;
    margin-right: 72px;
  }
}

.inputBox {
  position: relative;
}

.inputBox span {
  position: absolute;
  top: 1px;
  left: 0px;
  display: inline-block;
  padding: 14px 0;
  font-size: 16px;
  color: $overall_color;
  font-weight: 300;
  transition: 0.5s;
  pointer-events: none;
}

.inputBox input:focus~span,
.inputBox input:invalid~span {
  font-size: 12px;
  color: $overall_color;
  transform: translateX(0px) translateY(-32px);
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

@media (max-width: 950px) {
  .wrap {
    .container {
      flex-direction: column;
    }
    footer {
      ul {
        li {
          margin-right: 20px;
        }
      }
    }
  }
}

@media (max-width: 540px) {
  .wrap {
    padding: 20px;
    .container {
      .left {
        .title {
          font-size: 40px;
          line-height: 40px;
          margin-bottom: 40px;
        }
        .description {
          margin-bottom: 40px;
        }
      }
      .right {
        form {
          margin-top: 50px;
        }
      }
    }
  }
}</style>
