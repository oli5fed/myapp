<template>
    <div class="home">
        <md-card id="card-home">
            <form @submit.prevent="sendData" id="main-form">
              <md-card-content>
                  <p class="thanks-content">
                      Заполните форму для регистрации на сайте
                  </p>
              </md-card-content>
                <md-input-container class="form-control">
                    <label>Имя</label>
                    <md-input v-model="name" id="name" type="text" />
                </md-input-container>

                <md-input-container class="form-control">
                    <label>e-mail</label>
                    <md-input v-model="email" id="email" type="email" />
                </md-input-container>



                <div class="form-control">
                    <label>Пол</label>
                    <br>
                    <md-radio v-model="gender" id="male" md-value="male" class="md-primary">муж</md-radio>
                    <md-radio v-model="gender" id="female" md-value="female" class="md-primary">жен</md-radio>
                </div>
                <div class="send-wrapper">
                    <md-button type="submit" class="md-raised md-primary" id="send">отправить</md-button>
                </div>
            </form>
        </md-card>
    </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'home',
  data: function() {
    return {
      name: '',
      email: '',
      gender: '',
    };
  },
  methods: {
    async sendData() {
      await axios({
            url: 'http://localhost:3000/api/records',
            method: 'post',
            data: {
                name: this.name,
                email: this.email,
                gender: this.gender
            }
          });

            this.$router.push('thanks');
            }
            }
            }
</script>

<style>
    .form-control:nth-child(4) {
        padding-left: 0;
    }

    .thanks-content {
        font-size: 16px;
        text-align: center;

    }

.md-card .md-card-content{
  background-color: blanchedalmond;
}
    .form-control:nth-child(4) > label {
        font-size: 17px;
        color: rgba(0, 0, 0, 0.6);
    }

    .send-wrapper {
        width: 100%;
        display: flex;
        justify-content: center;
    }

    #send {
        margin-top: 5px;
        margin-bottom: 10px;
    }

    #main-form {
        padding: 5px;
    }

    .home {
        width: 30%;
        min-width: 250px;
        opacity: 0;
        position: absolute;
        left: 50%;
        top: -100%;
        transform: translate(-50%);
        animation-name: home;
        animation-duration: .5s;
        animation-timing-function: linear;
        animation-fill-mode: forwards;
    }

    @keyframes home {
        from {
            opacity: 0;
            top: -100%;
        }
        to {
            opacity: 1;
            top: 16%;
        }
    }

    #card-home{
        background-color: rgba(255, 255, 255, 0.6);
    }
</style>
