<template>
  <div class="order">
    <!--    <p>ID {{ id }}</p>-->
    <!--    <p>npi not found {{ npiFound }}</p>-->
    <!--    <p>current step {{ currentStep }}</p>-->
    <template v-if="currentStep === 0">
      <npi-form />
    </template>
    <div
        v-if="!npiFound"
        class="l-container u-align--center"
    >
      <v-spacer size="quad" />
      <h1>NPI Not Found</h1>
      <p>Please use the form above to try again.</p>
      <v-spacer size="quad" />
    </div>
    <div v-if="currentStep > 0">
      <div class="order-hero">
        <h1>Prescription Pad Online Order Form</h1>
      </div>
      <div class="l-container">
        <v-spacer size="quad" />
        <form>
          <div
              v-if="currentStep===1"
              class="order-form-step1"
          >
            <h4 class="u-space--bottom">Step 1: Contact Information</h4>
            <div class="order-form l-grid l-grid--2up u-space--bottom">
              <div>
                <label class="u-space--bottom">First Name *
                  <input
                      v-model="firstName"
                      type="text"
                      :class="firstName==='' ? 'error' : ''"
                  >
                </label>
                <label class="u-space--bottom">Last Name *
                  <input
                      v-model="lastName"
                      type="text"
                      :class="lastName==='' ? 'error' : ''"
                  >
                </label>
              </div>
              <div>
                <label class="u-space--bottom">Email Address *
                  <input
                      v-model="email"
                      type="email"
                      :class="!validEmail(email) ? 'error' : ''"
                  >
                </label>
                <label class="u-space--bottom">Phone *
                  <input
                      v-model="phone"
                      type="text"
                      :class="phone==='' ? 'error' : ''"
                  >
                </label>
              </div>
            </div>
            <v-button
                @click="startOver"
                class="u-space--right"
            >
              Start Over
            </v-button>
            <v-button
                @click="validateStep1"
                @keypress.space.enter="validateStep1"
            >
              Continue To Step 2
            </v-button>
            <p
                class="error-message u-space--top"
                v-if="displayErrorMessage"
            >
              Please fill out the required information (highlighted in red above) to continue!
            </p>
          </div>
          <div
              v-if="currentStep===2"
              class="order-form-step2"
          >
            <h4 class="u-space--bottom">Step 2: Order Details</h4>
            <div class="l-grid l-grid--2up">
              <div>
                <label class="u-space--bottom">Pad/Prescription Type *
                  <select v-model="padType">
                    <option
                        value="One-Part"
                        selected
                    >
                      One-Part
                    </option>
                    <option value="Two-Part">Two-Part</option>
                    <option value="Upper Left Laser">Upper Left Laser</option>
                  </select>
                </label>
              </div>
              <div>
                <label class="u-space--double--bottom">Quantity *
                  <select v-model="quantity">
                    <option
                        value="1"
                        selected
                    >1
                    </option>
                    <option value="2">2</option>
                    <option value="3">3</option>
                    <option value="4">4</option>
                    <option value="5">5</option>
                  </select>
                </label>
              </div>
            </div>
            <v-button
                @click="currentStep=1"
                @keypress.space.enter="currentStep=1"
                class="secondary u-space--right"
            >Go Back
            </v-button>
            <v-button
                @click="currentStep=3"
                @keypress.space.enter="currentStep=3"
            >Continue To Step 3
            </v-button>
            <p
                class="error-message u-space--top"
                v-if="displayErrorMessage"
            >
              Please fill out the required information (highlighted in red above) to continue!
            </p>
          </div>
          <div
              v-if="currentStep===3"
              class="order-form-step3"
          >
            <h4 class="u-space--bottom">Step 3: Prescriber Details</h4>
            <p class="u-space--bottom">NPI Number: {{ id }}</p>
            <label class="u-space--bottom">Group Name (if applicable) or Facility Name *
              <input
                  type="text"
                  v-model="groupName"
                  :class="groupName==='' ? 'error' : ''"
              >
            </label>
            <label class="u-space--bottom">Prescriber's Name and Degree *
              <input
                  type="text"
                  v-model="prescriberName"
                  :class="prescriberName==='' ? 'error' : ''"
              >
            </label>
            <label class="u-space--bottom">Practice or Specialty *
              <input
                  type="text"
                  v-model="specialty"
                  :class="specialty==='' ? 'error' : ''"
              >
            </label>
            <label class="u-space--bottom">Address 1 *
              <input
                  type="text"
                  v-model="address1"
                  :class="address1==='' ? 'error' : ''"
              >
            </label>
            <label class="u-space--bottom">Address 2
              <input
                  type="text"
                  v-model="address2"
              >
            </label>
            <div class="l-grid l-grid--2up u-space--bottom">
              <div>
                <label class="u-space--bottom">City *
                  <input
                      type="text"
                      v-model="city"
                      :class="city==='' ? 'error' : ''"
                  >
                </label>
                <label class="u-space--bottom">Zip Code *
                  <input
                      type="text"
                      v-model="zip"
                      :class="zip==='' ? 'error' : ''"
                  >
                </label>
              </div>
              <div>
                <label class="u-space--bottom">State *
                  <select
                      v-model="state"
                      :class="state==='' ? 'error' : ''"
                  >
                    <option value="AL">Alabama</option>
                    <option value="AK">Alaska</option>
                    <option value="AZ">Arizona</option>
                    <option value="AR">Arkansas</option>
                    <option value="CA">California</option>
                    <option value="CO">Colorado</option>
                    <option value="CT">Connecticut</option>
                    <option value="DE">Delaware</option>
                    <option value="DC">District Of Columbia</option>
                    <option value="FL">Florida</option>
                    <option value="GA">Georgia</option>
                    <option value="HI">Hawaii</option>
                    <option value="ID">Idaho</option>
                    <option value="IL">Illinois</option>
                    <option value="IN">Indiana</option>
                    <option value="IA">Iowa</option>
                    <option value="KS">Kansas</option>
                    <option value="KY">Kentucky</option>
                    <option value="LA">Louisiana</option>
                    <option value="ME">Maine</option>
                    <option value="MD">Maryland</option>
                    <option value="MA">Massachusetts</option>
                    <option value="MI">Michigan</option>
                    <option value="MN">Minnesota</option>
                    <option value="MS">Mississippi</option>
                    <option value="MO">Missouri</option>
                    <option value="MT">Montana</option>
                    <option value="NE">Nebraska</option>
                    <option value="NV">Nevada</option>
                    <option value="NH">New Hampshire</option>
                    <option value="NJ">New Jersey</option>
                    <option value="NM">New Mexico</option>
                    <option value="NY">New York</option>
                    <option value="NC">North Carolina</option>
                    <option value="ND">North Dakota</option>
                    <option value="OH">Ohio</option>
                    <option value="OK">Oklahoma</option>
                    <option value="OR">Oregon</option>
                    <option value="PA">Pennsylvania</option>
                    <option value="RI">Rhode Island</option>
                    <option value="SC">South Carolina</option>
                    <option value="SD">South Dakota</option>
                    <option value="TN">Tennessee</option>
                    <option value="TX">Texas</option>
                    <option value="UT">Utah</option>
                    <option value="VT">Vermont</option>
                    <option value="VA">Virginia</option>
                    <option value="WA">Washington</option>
                    <option value="WV">West Virginia</option>
                    <option value="WI">Wisconsin</option>
                    <option value="WY">Wyoming</option>
                  </select>
                </label>
                <label class="u-space--bottom">Country *
                  <select
                      v-model="country"
                      :class="country==='' ? 'error' : ''"
                  >
                    <option
                        value="United States"
                        selected
                    >United States
                    </option>
                  </select>
                </label>
              </div>
            </div>
            <label class="u-space--bottom">License Number *
              <input
                  type="text"
                  v-model="licenseNumber"
                  :class="licenseNumber==='' ? 'error' : ''"
              >
            </label>
            <label class="u-space--bottom">DEA Registration Number *
              <input
                  type="text"
                  v-model="deaNumber"
                  :class="deaNumber==='' ? 'error' : ''"
              >
            </label>
            <fieldset class="u-space--bottom">
              <legend>Include DEA Number on the prescription?</legend>
              <input
                  type="radio"
                  name="includeDea"
                  value="yes"
                  id="yes"
                  v-model="includeDea"
              >
              <label for="yes">Yes</label>
              <input
                  type="radio"
                  name="includeDea"
                  value="no"
                  id="no"
                  v-model="includeDea"
              ><label for="no">No</label>
            </fieldset>
            <v-button
                @click="currentStep=2"
                @keypress.space.enter="currentStep=2"
                class="secondary u-space--right"
            >
              Go Back
            </v-button>
            <v-button
                @click="validateStep3"
                @keypress.space.enter="validateStep3"
            >
              Preview Submission
            </v-button>
            <p
                class="error-message u-space--top"
                v-if="displayErrorMessage"
            >
              Please fill out the required information (highlighted in red above) to continue!
            </p>
          </div>
          <div
              v-if="currentStep===4"
              ref="step4"
              class="order-form-step4"
          >
            <h4 class="u-space--bottom">Confirm Your Submission</h4>
            <div class="l-grid l-grid--2up">
              <div>
                <p class="u-space--bottom"><strong>Contact Information</strong></p>
                <span v-html="contactInformation" />
                <p class="u-space--bottom u-space--top"><strong>Order Details</strong></p>
                <span v-html="orderDetails" />
              </div>
              <div>
                <p class="u-space--bottom"><strong>Prescriber Details</strong></p>
                <span v-html="prescriberDetails" />
              </div>
            </div>
            <v-button
                @click="currentStep===1"
                @keypress.enter.space="currentStep===1"
                class="secondary u-space--right"
            >
              Edit Information
            </v-button>
            <v-button
                @click="submitOrder"
                @keypress.enter.space="submitOrder"
            >
              Submit Order
            </v-button>
          </div>
        </form>
        <div
            v-if="currentStep===5"
            ref="step5"
            class="order-form-step5"
        >
          <h4 class="u-space--bottom">Your Order Has Been Submitted!</h4>
          <p>Thank you.</p>
        </div>
      </div>
      <v-spacer size="quad" />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import NpiForm from '../components/NpiForm'
import VButton from 'vue-evolve/src/components/VButton'
import VSpacer from 'vue-evolve/src/components/VSpacer'

export default {
  name: 'TheHeader',
  components: {
    NpiForm,
    VButton,
    VSpacer
  },
  data () {
    return {
      npiFound: true,
      currentStep: 0,
      displayErrorMessage: false,
      email: '',
      firstName: '',
      lastName: '',
      phone: '',
      info: null,
      id: null,
      padType: 'One-Part',
      quantity: 1,
      groupName: '',
      prescriberName: '',
      specialty: '',
      address1: '',
      address2: '',
      city: '',
      zip: '',
      state: 'NJ',
      country: 'United States',
      licenseNumber: '',
      deaNumber: '',
      includeDea: 'yes'
    }
  },
  mounted () {
    if (this.$route.query.ID) {
      this.id = this.$route.query.ID
      axios
          .get('http://165.227.100.233/npi/' + this.id || this.$route.query.ID)
          .then(response => (this.setData(response.data)))
          .catch(function (error) {
            console.log(error)
          })
    }
  },
  watch: {
    '$route.query.ID' () {
      if (this.$route.query.ID) this.id = this.$route.query.ID
      if (this.id > 0) this.currentStep = 1
    },
    id () {
      axios
          .get('http://165.227.100.233/npi/' + this.id || this.$route.query.ID)
          .then(response => (this.setData(response.data)))
          .catch(function (error) {
            console.log(error)
          })
    }
  },
  computed: {
    contactInformation () {
      return `
      <table>
        <tr>
          <td>First Name:</td>
          <td>` + this.firstName + `</td>
        </tr>
        <tr>
          <td>Last Name:</td>
          <td>` + this.lastName + `</td>
        </tr>
        <tr>
          <td>Phone:</td>
          <td>` + this.phone + `</td>
        </tr>
        <tr>
          <td>Email</td>
          <td>` + this.email + `</td>
        </tr>
      </table>
      `
    },
    orderDetails () {
      return `
      <table class="u-space--bottom">
        <tr>
          <td>Pad/Prescription Type:</td>
          <td>` + this.padType + `</td>
        </tr>
        <tr>
          <td>Quantity:</td>
          <td>` + this.quantity + `</td>
        </tr>
      </table>
      `
    },
    prescriberDetails () {
      return `
      <table>
        <tr>
          <td>Group Name / Facility Name:</td>
          <td>` + this.groupName + `</td>
        </tr>
        <tr>
          <td>Prescriber's Name and Degree:</td>
          <td>` + this.prescriberName + `</td>
        </tr>
        <tr>
          <td>Practice or Specialty:</td>
          <td>` + this.specialty + `</td>
        </tr>
        <tr>
          <td>Address 1:</td>
          <td>` + this.address1 + `</td>
        </tr>
        <tr>
          <td>Address 2:</td>
          <td>` + this.address2 + `</td>
        </tr>
        <tr>
          <td>City:</td>
          <td>` + this.city + `</td>
        </tr>
        <tr>
          <td>State:</td>
          <td>` + this.state + `</td>
        </tr>
        <tr>
          <td>Country</td>
          <td>` + this.country + `</td>
        </tr>
        <tr>
          <td>License Number</td>
          <td>` + this.licenseNumber + `</td>
        </tr>
        <tr>
          <td>NPI Number</td>
          <td>` + this.id + `</td>
        </tr>
        <tr>
          <td>DEA Registration Number</td>
          <td>` + this.deaNumber + `</td>
        </tr>
        <tr>
          <td>Include DEA Number on the prescription?</td>
          <td>` + this.includeDea + `</td>
        </tr>
      </table>
      `
    }
  },
  methods: {
    setData (data) {
      if (data.results && data.results.length > 0) {
        this.info = data.results[0]
        this.firstName = data.results[0].basic.first_name
        this.lastName = data.results[0].basic.last_name
        this.phone = data.results[0].practiceLocations ? data.results[0].practiceLocations[0].telephone_number : ''
        this.address1 = data.results[0].practiceLocations ? data.results[0].practiceLocations[0].address_1 : ''
        this.address2 = data.results[0].practiceLocations ? data.results[0].practiceLocations[0].address_2 : ''
        this.city = data.results[0].practiceLocations ? data.results[0].practiceLocations[0].city : ''
        this.zip = data.results[0].practiceLocations ? data.results[0].practiceLocations[0].postal_code : ''
        this.state = data.results[0].practiceLocations ? data.results[0].practiceLocations[0].state : ''
        this.country = data.results[0].practiceLocations ? data.results[0].practiceLocations[0].country_name : 'United States'
        if (data.results[0].identifiers) {
          if (data.results[0].identifiers.length > 0) {
            const deaInfo = data.results[0].identifiers.filter(item => item.issuer === 'DEA')
            const licenseInfo = data.results[0].identifiers.filter(item => item.issuer === 'CDS')
            this.deaNumber = deaInfo.length > 0 ? deaInfo[0].identifier : ''
            this.licenseNumber = licenseInfo.length > 0 ? licenseInfo[0].identifier : ''
          }
        }
        let prescriberNameString = ''
        if (data.results[0].basic.name_prefix) prescriberNameString += data.results[0].basic.name_prefix + ' '
        if (data.results[0].basic.first_name) prescriberNameString += data.results[0].basic.first_name + ' '
        if (data.results[0].basic.last_name) prescriberNameString += data.results[0].basic.last_name + ' '
        if (data.results[0].basic.credential) prescriberNameString += data.results[0].basic.credential
        this.prescriberName = prescriberNameString
        this.specialty = data.results[0].taxonomies[0].desc
        // handle NPI-2 data
        if (data.results[0].enumeration_type === 'NPI-2') {
          this.groupName = data.results[0].basic.organization_name
          this.prescriberName = ''
        }
        this.currentStep = 1
        this.npiFound = true
      }
      else {
        this.npiFound = false
        this.currentStep = 0
      }
    },
    startOver () {
      this.id = ''
      this.npiFound = true
      this.currentStep = 0
    },
    validateStep1 () {
      if (
          this.firstName !== '' &&
          this.lastName !== '' &&
          this.phone !== '' &&
          this.validEmail(this.email)
      ) {
        this.displayErrorMessage = false
        this.currentStep = 2
      } else {
        this.displayErrorMessage = true
      }
    },
    validateStep3 () {
      if (
          this.groupName !== '' &&
          this.prescriberName !== '' &&
          this.specialty !== '' &&
          this.address1 !== '' &&
          this.city !== '' &&
          this.zip !== '' &&
          this.state !== '' &&
          this.country !== '' &&
          this.licenseNumber !== '' &&
          this.id > 0 &&
          this.deaNumber !== ''
      ) {
        this.displayErrorMessage = false
        this.currentStep = 4
        this.$nextTick(() => {
          this.$refs.step4.scrollIntoView();
        })
      } else {
        this.displayErrorMessage = true
      }
    },
    submitOrder () {
      this.currentStep = 5
      this.$nextTick(() => {
        this.$refs.step5.scrollIntoView();
      })
      console.log('order submitted')
      axios({
        method: 'post',
        url: 'https://api.emailjs.com/api/v1.0/email/send/',
        data: {
          service_id: 'service_n1nlx9r',
          template_id: 'template_e5mh7zg',
          user_id: 'user_s0M53u6qxQpT90KoWRp78',
          template_params: {
            'subject': 'new order from rxprovisions.com',
            'message': this.contactInformation + '<br><br>' + this.orderDetails + '<br><br>' + this.prescriberDetails,
            'to': 'mail@rxprovisions.com',
            'from_name': 'rxprovisions.com',
          }
        }
      })
    },
    validEmail: function (email) {
      let re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    }
  }
}
</script>

<style lang="scss">
.order {
  background-color: var(--color-light-gray);

  h1 {
    margin-bottom: var(--space-4);
  }

  .secondary {
    --button-background: var(--color-white);
    --button-text: var(--color-secondary);
    --button-border: 2px solid var(--color-secondary);
    --button-background-hover: var(--color-secondary);
    --button-text-hover: var(--color-white);
    --button-border-hover: 2px solid var(--color-secondary);
  }

  .error-message {
    color: red;
    font-size: var(--font-size-4);
    font-weight: bold;
  }

  .error {
    border: solid 1px red;
  }
}

.order-hero {
  display: flex;
  align-items: center;
  justify-content: center;
  background: url("/images/order-hero.jpg") no-repeat;
  background-size: cover;
  height: 300px;

  h1 {
    color: var(--color-white);
    text-shadow: 0 0 20px var(--color-black);
    text-align: center;
  }
}
</style>
