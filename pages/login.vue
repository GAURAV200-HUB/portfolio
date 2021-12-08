<template>
  <v-img
    :src="`https://assets.hongkiat.com/uploads/minimalist-mobile-wallpapers/original/09.jpg`"
    :lazy-src="`https://assets.hongkiat.com/uploads/minimalist-mobile-wallpapers/original/09.jpg`"
    class="fill-height login"
    center
    height="100vh"
    alt="login background"
  >
    <!-- <v-container fluid class="fill-height"> -->
    <v-row align="center" justify="center">
      <v-col cols="12" sm="8" md="5" lg="5">
        <v-card-text class="text-center">
          <div class="header">
            <nuxt-link hreflang="en" to="/demo">
              <v-img
                :src="require('@/assets/Fairplay_New_Logo.png')"
                :lazy-src="require('@/assets/Fairplay_New_Logo.png')"
                max-width="100%"
                height="75"
                contain
                alt="fairplay logo"
                class="mt-10 mb-10"
              ></v-img>
            </nuxt-link>
          </div>
          <div class="navigation pl-5">
            <div
              v-if="signIn"
              class="d-flex justify-content-start align-items-center"
            >
              <div @click="back()">
                <v-icon large>mdi-chevron-left</v-icon>
              </div>
              <div>
                <h6 style="color: white; margin: 0 0 1px 0; padding: 0">
                  Sign In
                </h6>
              </div>
            </div>
            <div
              v-if="register"
              class="d-flex justify-content-start align-items-center"
            >
              <div @click="back()">
                <v-icon large>mdi-chevron-left</v-icon>
              </div>
              <div>
                <h6 style="color: white; margin: 0 0 1px 0; padding: 0">
                  Register
                </h6>
              </div>
            </div>
          </div>
          <div class="forms">
            <div v-if="signIn" class="pa-5">
              <v-form ref="loginForm" lazy-validation @submit.prevent="">
                <div class="d-flex justify-content-between align-items-center">
                  <v-icon color="#f36c21" class="my-1 mr-2">mdi-account</v-icon>
                  <country-code
                    v-model="countryCode"
                    class="mr-2 mt-n1 flex-grow-0"
                  />
                  <v-text-field
                    label="Email or Mobile Number"
                    color="#f36c21"
                    class="form-input"
                    :rules="rules.userName"
                    :dark="true"
                    required
                  ></v-text-field>
                </div>
                <div class="d-flex login-password">
                  <v-icon color="#f36c21" class="my-1 mr-2">mdi-lock</v-icon>
                  <v-text-field
                    :append-icon="showPassword ? 'mdi-eye-off' : 'mdi-eye'"
                    :type="showPassword ? 'text' : 'password'"
                    label="Password"
                    color="#f36c21"
                    :rules="rules.password"
                    required
                    @click:append="showPassword = !showPassword"
                    @click="showExample = false"
                  ></v-text-field>
                </div>
                <v-row
                  no-gutters
                  class="mt-3 d-flex justify-content-between align-items-center"
                >
                  <v-col cols="6" class="no-margin no-padding">
                    <div class="custom-checkbox text-left ml-1">
                      <input id="rememberMe" type="checkbox" />
                      <label for="rememberMe">Remember me</label>
                    </div>
                  </v-col>
                  <v-col cols="6">
                    <div class="d-flex justify-end">
                      <v-btn
                        to="/forgot-password"
                        class="forgotPassword"
                        small
                        text
                      >
                        Forgot password?
                      </v-btn>
                    </div>
                  </v-col>
                </v-row>
                <div class="mt-10">
                  <v-btn color="#f36c21" class="pa-5 sinIn-btn" dark>
                    Sign In
                  </v-btn>
                </div>
              </v-form>
              <div
                class="
                  m-4
                  socialLogin
                  d-flex
                  justify-content-evenly
                  align-items-center
                "
              >
                <div>
                  <v-btn tile>
                    <v-icon left color="#f36c21"> mdi-facebook </v-icon>
                    <span style="color: #f36c21"> Facebook</span>
                  </v-btn>
                </div>
                <div>
                  <v-btn tile>
                    <v-icon left color="#f36c21"> mdi-google </v-icon>
                    <span style="color: #f36c21"> Google </span>
                  </v-btn>
                </div>
              </div>
              <div class="d-flex justify-content-center align-items-center">
                <div>
                  <v-card-text
                    class="pa-0 mt-4 mb-2 text-center"
                    style="color: white"
                    >Not a member?</v-card-text
                  >
                </div>
                <div>
                  <v-card-text
                    class="pa-0 ml-1 mt-4 mb-2 text-center joinNow-btn"
                    >Join Now</v-card-text
                  >
                </div>
              </div>
            </div>
            <div v-if="register" class="pa-5">
              <v-form ref="loginForm" lazy-validation @submit.prevent="">
                <div class="d-flex justify-content-between align-items-center">
                  <v-icon color="#f36c21" class="my-1 mr-2">mdi-account</v-icon>
                  <v-text-field
                    label="Name* "
                    color="#f36c21"
                    class="form-input"
                    :rules="rules.userName"
                    :dark="true"
                    required
                  ></v-text-field>
                </div>
                <div class="d-flex justify-content-between align-items-center">
                  <v-icon color="#f36c21" class="my-1 mr-2">mdi-phone</v-icon>
                  <v-text-field
                    type="number"
                    label="Mobile Number* "
                    color="#f36c21"
                    class="form-input"
                    :rules="rules.userName"
                    :dark="true"
                    required
                  ></v-text-field>
                </div>
                <div class="d-flex justify-content-between align-items-center">
                  <v-icon color="#f36c21" class="my-1 mr-2">mdi-gmail</v-icon>
                  <v-text-field
                    type="email"
                    label="Email* "
                    color="#f36c21"
                    class="form-input"
                    :rules="rules.userName"
                    :dark="true"
                    required
                  ></v-text-field>
                </div>
                <div class="d-flex login-password">
                  <v-icon color="#f36c21" class="my-1 mr-2">mdi-lock</v-icon>
                  <v-text-field
                    :append-icon="showPassword ? 'mdi-eye-off' : 'mdi-eye'"
                    :type="showPassword ? 'text' : 'password'"
                    label="Password* "
                    color="#f36c21"
                    :rules="rules.password"
                    required
                    @click:append="showPassword = !showPassword"
                    @click="showExample = false"
                  ></v-text-field>
                </div>
                <div class="mt-10">
                  <v-btn color="#f36c21" class="pa-5 sinIn-btn" dark>
                    Register
                  </v-btn>
                </div>
              </v-form>
              <div class="d-flex justify-content-center align-items-center">
                <div>
                  <v-card-text
                    class="pa-0 mt-4 mb-2 text-center"
                    style="color: white"
                    >By registring, I agree to Sportslive's
                  </v-card-text>
                </div>
                <div>
                  <v-card-text
                    class="pa-0 ml-1 mt-4 mb-2 text-center joinNow-btn"
                    >T&Cs</v-card-text
                  >
                </div>
              </div>
            </div>
          </div>
          <div v-if="signIn" class="footer mb-3">
            <div class="mt-10 d-flex justify-content-center align-items-center">
              <span class="loginBootom-btn"
                >Privacy Policy <span> | </span>
                <span class="loginBootom-btn">Terms and Condition</span></span
              >
            </div>
          </div>
          <div v-if="register" class="footer mb-3">
            <div class="mx-5 d-flex justify-content-between align-items-center">
              <div>Have a referral code?</div>
              <div>Already a user?</div>
            </div>
            <div class="mx-5 d-flex justify-content-between align-items-center">
              <div style="color: white">Enter Code</div>
              <div style="color: white">Log In</div>
            </div>
          </div>
        </v-card-text>
      </v-col>
    </v-row>
    <!-- </v-container> -->
  </v-img>
</template>

<script>
import CountryCode from '@/components/countryCode.vue'
export default {
  components: {
    CountryCode,
  },
  data() {
    return {
      msg: 'https://fairplay-image.fairplay.club',
      countryCode: '91',
      showPassword: false,
      signIn: false,
      register: true,
      rules: {
        userName: [(v) => !!v || 'Email / Mobile Number is required'],
        password: [
          (v) => !!v || 'Password is required',
          (v) =>
            !(v && v.length < 6) || 'Password must be of 6 characters or more',
          (v) =>
            !(v && v.split(' ').join('').length < v.length) ||
            'Password cannot contain spaces!',
        ],
        //   email: [
        //     (v) => !!v || 'Email is required',
        //     (v) =>
        //       /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(v) ||
        //       'Invalid Email Address',
        //   ],
      },
    }
  },
  methods: {
    back() {
      this.register = !this.register
      this.signIn = !this.signIn
    },
  },
}
</script>

<style lang="scss" scoped>
.login {
  color: #f36c21;
  .header {
    // display: flex;
    // justify-content: center;
    // align-items: center;
    position: fixed;
    height: 20%;
    top: 0;
    left: 0;
    right: 0;
  }
  .navigation {
    position: fixed;
    top: 20%;
    left: 0;
    right: 0;
    height: 10%;
  }
  .forms {
    // display: flex;
    // justify-content: center;
    // align-items: center;
    position: fixed;
    top: 25%;
    left: 0;
    right: 0;
    height: 50%;
  }
  .footer {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
  }
}
.primary--border {
  border: 2px solid #f36c21 !important;
  border-color: #f36c21 !important;
}
.bg-card-color-opacity {
  background-color: rgba(0, 0, 0, 0.75) !important;
}
.form-input input {
  text-transform: lowercase !important;
}
.login-password {
  position: relative;

  .v-input__append-inner {
    position: absolute;
    right: 6px;
  }
}
.custom-checkbox input {
  display: none;
  cursor: pointer;
}
.custom-checkbox label {
  color: white;
  position: relative;
  cursor: pointer;
}

.custom-checkbox label:before {
  content: '';
  -webkit-appearance: none;
  background-color: #010101;
  padding: 10px;
  display: inline-block;
  position: relative;
  vertical-align: middle;
  cursor: pointer;
  margin-right: 8px;
  border-radius: 4px;
}

.custom-checkbox input:checked + label:after {
  content: '';
  display: block;
  position: absolute;
  top: 6px;
  left: 8px;
  width: 5px;
  height: 12px;
  border: solid #f36c21;
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
}

.cursor-pointer {
  cursor: pointer;
}

.custom-checkbox .header-label:before {
  background-color: #fff;
  padding: 6px;
}

.custom-checkbox input:checked + .header-label:after {
  top: 4px;
  left: 4px;
  width: 4px;
  height: 7px;
}

.forgotPassword {
  text-transform: capitalize;
  font-weight: normal;
}

.no-margin {
  margin: 0 !important;
}

.no-padding {
  padding: 0 !important;
}

.sinIn-btn {
  border-radius: 15px;
}

.joinNow-btn {
  color: #f36c21;
  font-size: 16px;
  cursor: pointer;
}

.loginBootom-btn {
  color: #f36c21;
  font-size: 14px;
  cursor: pointer;
}

.socialLogin {
  color: #f36c21;
}
</style>