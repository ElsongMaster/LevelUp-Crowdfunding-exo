<template>
  <div :class=" selected?'pledecardselect select-card':'pledecardselect'">
    <div class="ContentMain">
      <div @click="checkedCheckbox()"  class="checkbox-container"><span class="chekbox"> <span v-if="selected" class="checked"></span></span></div>
      <div class="textContent">
        <div class="title-container">
          <div class="title">
            <span class="title-name">Pledge with no reward</span>
            <span class="price"> Pledge $25 or more</span>
          </div>
          <div class="days-container">
            <span class="days">101<span class="left">left</span></span>
          </div>
        </div>
        <p>
          Choose to support us without a reward if you simply believe in our
          project. As a backer, you cill be signed up to receive product updates
          via email.
        </p>
      </div>
    </div>
    <div v-if="selected" class="inputPledge-container">
      <p>Enter your pledge</p>
      <div class="input-content">
        <div>$ <input type="text" name="" value="25" id="" /></div>
        <button>Continue</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PledgeCardSelect",

  data() {
    return {
      selected: false,
    };
  },

  methods:{
      checkedCheckbox(){
          if(!this.selected){
              
              this.selected = true;
          }else{
              this.selected = false;

          }
      }
  }
};
</script>

<style scoped lang="scss">
.pledecardselect {
  min-height: 125px;
  height: fit-content;
  border: 2px solid rgb(230, 227, 227);
  width: 100%;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  .ContentMain {
    display: flex;
    .checkbox-container {
      height: 100%;
      width: 10%;
      display: flex;
      justify-content: center;
      .chekbox {
        border: 2px solid rgb(230, 227, 227);
        height: 25px;
        width: 25px;
        border-radius: 50%;
        margin-top: 30%;
        display: flex;
        justify-content: center;
        align-items: center;

        .checked{
            height: 70%;

            width: 70%;
            background-color:rgb(21, 182, 171) ;
            border-radius: 50%;

        }
      }
      .chekbox:hover {
        cursor: url("data:image/x-icon;base64,AAACAAEAICACAAAAAAAwAQAAFgAAACgAAAAgAAAAQAAAAAEAAQAAAAAAgAAAAAAAAAAAAAAAAgAAAAAAAAAAAAAA////AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/gAAAf4AAAPVAAAH1QAAB9WAAA3VgAAd/4AAGbaAAAG2gAABtgAAAYAAAAGAAAABgAAAAYAAAAAAAAA//////////////////////////////////////////////////////////////////////////////////////gD///4A///8AP//+AB///AAf//wAD//4AA//8AAP//AAD//5AA///wAf//8Af///D////w////8P////n///8="),
          auto;
      }
    }
    .textContent {
      height: 100%;
      width: 80%;
      padding: 20px 5px;
      // border: 2px solid green;
      * {
        font-size: 12px;
      }
      .title-container {
        display: flex;
        justify-content: space-between;

        .title {
          width: 60%;
          display: flex;
          justify-content: space-between;
          .title-name {
            font-weight: bold;
          }
          .price {
            color: rgb(21, 182, 171);
          }
        }
        .days-container {
          .days {
            font-size: 15px;
            font-weight: bold;
          }
          .left {
            padding-left: 5px;
            color: rgb(189, 187, 187);
          }
        }
      }
    }
  }
  .inputPledge-container {
    border-top: 2px solid rgb(231, 222, 222);
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    p{
        padding-left: 10px;
    }
    .input-content {
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      div{
          margin-right: 5px;
          display: flex;
          border:2px solid rgb(231, 222, 222);
          padding: 5px;
          width: 80px;
          border-radius: 30px;
          justify-content: center;
          font-size: 14px;
          color:rgb(231, 222, 222) ;
          input{
              color: black;
              padding-left: 5px;
              width: fit-content;
              width: 30px;
              background-color: transparent;
          }
      }
      button {
        background-color: rgb(31, 179, 169);
        color: white;
        padding: 0.5em 1.2em;
        border-radius: 30px;
        font-size: 12px;
      }
      button:hover {
        cursor: url("data:image/x-icon;base64,AAACAAEAICACAAAAAAAwAQAAFgAAACgAAAAgAAAAQAAAAAEAAQAAAAAAgAAAAAAAAAAAAAAAAgAAAAAAAAAAAAAA////AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/gAAAf4AAAPVAAAH1QAAB9WAAA3VgAAd/4AAGbaAAAG2gAABtgAAAYAAAAGAAAABgAAAAYAAAAAAAAA//////////////////////////////////////////////////////////////////////////////////////gD///4A///8AP//+AB///AAf//wAD//4AA//8AAP//AAD//5AA///wAf//8Af///D////w////8P////n///8="),
          auto;
      }
    }
  }
}
.select-card {
  border-color: rgb(21, 182, 171) !important;
}
</style>
