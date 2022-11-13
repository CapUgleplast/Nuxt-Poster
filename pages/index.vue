<template>
  <div>
    <div class="row">

      <ul class="list-group list-group-numbered">
        <li class="list-group-item d-flex justify-content-between ">
            <img src="~/assets/ava1.png" class="avatar avatar-one" alt="">
            <textarea v-model="postText" class="form-control textInput" @focus="inputOnFocus=true" placeholder="Создайте новый пост" id="floatingTextarea"></textarea>
            <button type="button" class="btn btn-outline-primary pinButt"  data-bs-toggle="button" autocomplete="off" v-if="!inputOnFocus"><img src="~/assets/pinButton.png" class="pin"></button>
        </li>

        <li class="list-group-item d-flex justify-content-between button-group-lower animated" v-if="inputOnFocus">
          <button type="button" class="btn btn-outline-primary lower-button lower-pic" data-bs-toggle="button" autocomplete="off"><img src="~/assets/pic.png" class="lower-icon"></button>
          <button type="button" class="btn btn-outline-primary lower-button lower-vid" data-bs-toggle="button" autocomplete="off"><img src="~/assets/vid.png" class="lower-icon"></button>
          <button type="button" class="btn btn-outline-primary lower-button lower-music" data-bs-toggle="button" autocomplete="off"><img src="~/assets/music.png" class="lower-icon"></button>
          <button type="button" class="btn btn-outline-primary lower-button lower-file" data-bs-toggle="button" autocomplete="off"><img src="~/assets/file.png" class="lower-icon"></button>
          <button type="button" class="btn btn-outline-primary lower-button lower-quiz" data-bs-toggle="button" autocomplete="off"><img src="~/assets/quiz.png" class="lower-icon"></button>
          <button type="button" class="btn btn-outline-primary lower-plan" data-bs-toggle="button" autocomplete="off">Запланировать  ∨</button>


            <button type="button" class="btn btn-outline-primary lower-visible animated" data-bs-toggle="button" autocomplete="off">
              <div class="vis mx-2" v-on:click="visibilityOnFocus = !visibilityOnFocus">Видно всем  ∨</div>
                <div class="card card-visibility" v-if="visibilityOnFocus">
                  <div class="card-body">
                    <div class="btn-group-vertical btn-group-visibility" role="group" aria-label="Vertical button group">
                      <button type="button" class="btn btn-primary-outline visibility-text"><div class="form-check">
                        <input class="form-check-input visibility-input" type="checkbox" id="formSwitchCheckDefault">
                        <label class="form-check-label visibility-label" for="formSwitchCheckDefault">Видно всем</label>
                      </div>
                      </button>
                      <button type="button" class="btn btn-primary-outline grey visibility-text"><div class="form-check">
                        <input class="form-check-input visibility-input" type="checkbox" id="formSwitchCheckDefault1">
                        <label class="form-check-label visibility-label label-members-only" for="formSwitchCheckDefault1">Только участникам</label>
                      </div>
                      </button>
                      <button type="button" class="btn btn-primary-outline visibility-text">
                        <div class="form-check">
                          <input class="form-check-input visibility-input" type="checkbox" id="formSwitchCheckDefault2">
                          <label class="form-check-label visibility-label" for="formSwitchCheckDefault2">Только мне</label>
                        </div>
                      </button>
                    </div>
                  </div>
                </div>
            </button>


          <button type="button" class="btn btn-outline-primary lower-button lower-options animated" data-bs-toggle="button" autocomplete="off">
            <img src="~/assets/options.png" class="lower-icon" v-on:click="optionsOnFocus = !optionsOnFocus">
            <div class="card" v-if="optionsOnFocus">
            <div class="card-header">
              <div class="btn-group dropright">
                <button type="button" class="btn btn-primary-outline dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false">
                  Выбрать тематику
                </button>
                <ul class="dropdown-menu">
<!--              <li><a class="dropdown-item" href="#">Action</a></li>
                  <li><a class="dropdown-item" href="#">Another action</a></li>
                  <li><a class="dropdown-item" href="#">Something else here</a></li>-->
                </ul>
              </div>
            </div>
            <div class="card-body">
              <div class="form-check form-switch">
                <label class="form-check-label" for="formSwitchCheckDefault">Не уведомлять</label>
                <input class="form-check-input" type="checkbox" id="formSwitchCheckDefault">
              </div>
              <div class="form-check form-switch">
                <label class="form-check-label" for="formSwitchCheckDefault1">Отключить комментарии</label>
                <input class="form-check-input" type="checkbox" id="formSwitchCheckDefault1">
              </div>
            </div>
          </div>
          </button>
          <button type="button" v-on:click="postIt" class="btn btn-primary postButt">Опубликовать</button>
        </li>
      </ul>
    </div>

    <div id="wrap" class="container postCard animated">
       <post-block class="animated" v-for="post in postHistory" :post-main="post" ></post-block>
    </div>
  </div>
</template>

<script>
import postBlock from "../components/postBlock";

export default {
  name: 'IndexPage',
  data:() => ({
    postInput: document.getElementsByClassName("textInput"),
    inputOnFocus: false,
    optionsOnFocus: false,
    visibilityOnFocus: false,
    postHistory: [],
    postText: null,
    checked1: false,
    checked2: false,
    checked3: false,
  }),
  components:{
   postBlock
  },
  methods:{
    postIt: function (){
      if(this.postText != null) {
        this.postHistory = Array.prototype.slice.call(this.postHistory);
        this.postHistory.unshift(this.postText);
        this.postText = null;
        console.log(this.postHistory);
        setTimeout(() => {
          this.inputOnFocus = false;
        }, 100)

      }
    }
  }
}
</script>

<style scoped>

.animated{
  -webkit-transition: all 1s linear 0s;
  -moz-transition: all 1s linear 0s;
  -o-transition: all 1s linear 0s;
  transition: all 1s linear 0s;
}

.visibility-label{
  position: absolute;
  right: 60px;
  top: -10px;
}

.label-members-only{
  transform: translateX(48px);
}

.visibility-input{
  position: absolute;
  transform: translateX(-162px);
  top: -12px;
}

.card-header{
  background: none;
  height: 56px;
}

.form-check-label{
  margin-bottom: 15px;
  color: #475569 !important;
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 20px;
}
.form-check-input{
  left: 110%;
}

.form-switch{
  position: relative;
  text-align: left;
  bottom: 6px;
  right: 20px;
}

.dropdown-toggle{
  height: 55px;
  width: 250px;
  right: 15px;
  bottom: 12px;
  text-align: left;
  color: #475569 !important;
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 20px;
}

.check{
  position: absolute;
  width: 20px;
  height: 20px;
  right: 158px;
}

.btn:focus{
  outline: none !important;
  box-shadow: none !important;
}

.btn-group-visibility{
  height: 168px;
  bottom: 20px;
  width: 198px;
  right: 20px;
}

.visibility-text{
  font-size: 14px;
  text-align: left;
}

.visibility-text:hover{
  background-color: #f8f8f8;
}

.grey{
  background-color: #F9F9F9;
}

.card{
  position: absolute;
  width: 277px;
  height: 152px;
  right: 0px;
  bottom: 30px;
  border-radius: 16px;
  box-shadow: 0px 0px 12px rgba(83, 83, 89, 0.12);
}

.vis{
  z-index: 50;
  padding-top: 5px;
  padding-bottom: 5px;
}

.card-visibility{
  right: 28%;
  height: 168px;
  margin-right: 100px;
  bottom: 50px;
  width: 200px;

}


.lower-button{
  position: relative;
  width: 20px;
  height: 25px;
  top: 10px;
  background: none !important;
  outline: none;
  border: none;
  box-shadow: none !important;
}


.lower-button:hover{
  color: #18191F;
}

.lower-pic{
  left:5px;
}

.lower-vid{
  left: 25px;
}

.lower-music{
  left: 45px;
}

.lower-icon{
  position: relative;
  width: 20px;
  height: 20px;
  right: 10px;
  bottom: 8px;
}

.lower-file{
  left: 65px;
}

.lower-quiz{
  left: 85px;
}

.lower-options{
  left: 140px;
}

.lower-plan{
  position: relative;
  left: 107px;
  color: #475569 !important;
  border-bottom: none;
  border-top: none;
  border-right: none;
  border-radius: 0px;
  padding-left: 20px;
  padding-right: 40px;
  background: none !important;
  border-color: #E8E6E6;
  box-shadow: none !important;
  white-space: nowrap;
}

.lower-visible{
  top: 5px;
  margin-left: 90px;
  color: #475569 !important;
  border-bottom: none;
  border-top: none;
  border-right: none;
  border-radius: 0px;
  background: none !important;
  border-color: #E8E6E6;
  box-shadow: none !important;
  white-space: nowrap;
}


.postCard{
  width: 60%;
  margin-left: 0px;
}


.input-group{
  margin-top: 3%;
  box-shadow: 0px 0px 12px rgba(83, 83, 89, 0.12);
  width: 60%;
  height: 80px;
  border-radius: 16px;
  border: 1px solid #E8E6E6;
}

.list-group{
  width: 900px;
  margin-top: 3%;
  box-shadow: 0px 0px 12px rgba(83, 83, 89, 0.12);
  border-radius: 16px;
}

.list-group-item{
  height: 80px;
}

.button-group-lower{
  transition: all 1s ease-in-out;
  height: 70px;

}

.postButt{
  width: 147px;
  height: 40px;
  margin-left: 18%;
  margin-top: 2px;
  background: #43A5D2;
  border-radius: 10px;
  outline: none !important;
  border: none !important;
  box-shadow: none !important;
}

.postButt:active:focus{
  background: #2e79a4;
}

.textInput{
  margin-top: 10px;
  margin-right: 20px;
  margin-left: 10px;
  border: black;
  height: auto;
  font-size: 15px;
  line-height: 24px;
  resize: none;
  display: flex;
}

.form-control:focus{
  outline: none !important;
  box-shadow: none !important;
}

.pinButt{
  background: none !important;
  outline: none !important;
  border-color: white !important;
  width: 40px;
  height: 40px;
  margin-right: 10px;
  margin-top: 7px;
  margin-bottom: 10px;
  box-shadow: none !important;
}

.pin{
  position: relative;
  width: 20px;
  height: 20px;
  right: 2px;
}

.avatar{
  position: relative;
  border-radius: 12px;
}

.avatar-one{
  width: 40px;
  height: 40px;
  left: 0px;
  top: 7px;
  bottom: 10px;
}
</style>
