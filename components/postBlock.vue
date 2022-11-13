<template>
  <div class="row">
    <div class="card animated">
      <div class="card-header">
        <img src="~/assets/ava1.png" class="avatar card-avatar">
        <button type="button" class="btn btn-outline-primary options"  data-bs-toggle="button" autocomplete="off">...</button>
        <p class="posterName">Строительство частных домов</p>
        <p class="posterName postDate">Опубликовано только что</p>
      </div>
      <div class="card-body">
        <p class="card-text">{{postMain}}</p>
      </div>
      <div class="card-footer text-muted">
        <img src="~/assets/ava2.png" class="avatar lower-avatar rounded-circle ">
        <input type="text" class="form-control comment" placeholder="Написать комментарий" aria-label="Username" aria-describedby="input-group-button-right">
        <button type="button" class="btn btn-outline-primary pinButt"  data-bs-toggle="button" autocomplete="off"><img src="~/assets/pinButton.png" class="pin"></button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "postBlock",
  props: ['postMain']
}
</script>

<style scoped>

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
  position: absolute;
  width: 20px;
  height: 20px;
  right: 62px;
  bottom: 34px;
}

.animated{
  -webkit-transition: all 1s linear 0s;
  -moz-transition: all 1s linear 0s;
  -o-transition: all 1s linear 0s;
  transition: all 1s linear 0s;
}

.avatar{
  position: relative;
  border-radius: 16px;
}

.posterName{
  position: relative;
  top: -36px;
  left: 109px;
  font-weight: 500;
  font-size: 16px;
  line-height: 20px;
}

.options{
  position: relative;
  left: 85%;
  top: -4px;
  background: none !important;
  border: none !important;
  outline: none !important;
  box-shadow: none !important;
  color: #94A2B3;
  font-size: 30px;
  z-index: 100;
}

.options:hover{
  color: #757B82 !important;
}

.postDate{
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 16px;
  color: #757B82;
  top: -43px;
}

.lower-avatar{
  position: absolute;
  width: 52px;
  height: 52px;
  left: 50px;
  margin-top: 7px;
}

.card{
  margin-top: 30px;
  width: 900px;
  margin-left: -15px;
  border: 1px solid #E8E6E6;
  box-shadow: 0px 0px 12px rgba(83, 83, 89, 0.12);
  border-radius: 16px;
}

.card-body{
  position: relative;
  left: 30px;
  top: 10px;
  height: auto;
}

.card-text{
  font-weight: 400;
  font-size: 15px;
  line-height: 24px;
  color: #18191F;
  width: 94%;
}

.card-header{
  border-bottom: none;
  background: white;
  border-radius: 16px;
  height: 23%;
}

.card-footer{
  background: white;
  border-bottom-left-radius: 16px;
  border-bottom-right-radius: 16px;
  height: 92px;
}

.card-avatar{
  width: 60px;
  height: 60px;
  top: 18px;
  left: 30px;
}

.comment{
  position: relative;
  width: 85%;
  left: 100px;
  height: 52px;
  top: 8px;
  background: #F8F8F8;
  border: 1px solid #EBEDF5;
  border-radius: 10px;
  font-weight: 400;
  font-size: 15px;
  line-height: 24px;
}


</style>
