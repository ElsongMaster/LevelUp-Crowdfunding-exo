<template>
  <div
    :class="
      pledgeData.isSelected
        ? 'pledecardselect select-card'
        : pledgeData.days == 0
        ? ' pledecardselect zero-days'
        : 'pledecardselect'
    "
  >
    <div class="ContentMain">
      <div @click="checkedCheckbox(index)" class="checkbox-container">
        <span class="chekbox">
          <span v-if="pledgeData.isSelected" class="checked"></span
        ></span>
      </div>
      <div class="textContent">
        <div class="title-container">
          <div class="title">
            <span class="title-name" @click="checkedCheckbox(index)">{{
              pledgeData.nom
            }}</span>
            <span v-if="pledgeData.price != null" class="price">
              Pledge ${{ pledgeData.price }} or more</span
            >
          </div>
          <div class="days-container">
            <span v-if="pledgeData.days != null" class="days"
              >{{ pledgeData.days }}<span class="left">left</span></span
            >
          </div>
        </div>
        <p>
          Choose to support us without a reward if you simply believe in our
          project. As a backer, you cill be signed up to receive product updates
          via email.
        </p>
      </div>
    </div>
    <div
      v-if="pledgeData.isSelected "
      class="inputPledge-container"
    >
      <p v-show=" pledgeData.isGivenReward">Enter your pledge</p>
      <div class="input-content">
        <div  v-show=" pledgeData.isGivenReward">
          $ <input id="priceChoose" type="text" name="" :value="pledgeData.price"  />
        </div>
        <button @click="sendPriceChoose()">Continue</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PledgeCardSelect",
  props: {
    pledgeData: Object,
    isGivenReward: Boolean,
    selected:Boolean,
    Index:Number
  },


  data() {
    return {
      indexPledge:null
    };
  },

created: function(){
    this.selected = this.pledgeData.isSelected;
    this.indexPledge = this.pledgeData.index
},

  computed:{
      getIsSelected(){

          let isSelected = this.pledgeData.isSelected;
          return isSelected

      }
  },

  methods: {
    checkedCheckbox() {
    //     console.log('checkedCheckbox',this.indexPledge)
    //   if (!this.selected) {
    //     this.selected = true;
    //   } else {
    //     this.selected = false;
    //   }
      this.$emit('checkBoxIndex',this.indexPledge)
    },

    sendPriceChoose(){

        let price = document.getElementById('priceChoose').value!=''?document.getElementById('priceChoose').value:null;
        this.$emit('getPrice',[true, price] )
    }


  },
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
  margin: 10px 0;
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

        .checked {
          height: 70%;

          width: 70%;
          background-color: rgb(21, 182, 171);
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
          .title-name:hover {
            cursor: url("data:image/x-icon;base64,AAACAAEAICACAAAAAAAwAQAAFgAAACgAAAAgAAAAQAAAAAEAAQAAAAAAgAAAAAAAAAAAAAAAAgAAAAAAAAAAAAAA////AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/gAAAf4AAAPVAAAH1QAAB9WAAA3VgAAd/4AAGbaAAAG2gAABtgAAAYAAAAGAAAABgAAAAYAAAAAAAAA//////////////////////////////////////////////////////////////////////////////////////gD///4A///8AP//+AB///AAf//wAD//4AA//8AAP//AAD//5AA///wAf//8Af///D////w////8P////n///8="),
              auto;
            color: rgb(21, 182, 171);
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
    p {
      padding-left: 10px;
    }
    .input-content {
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      div {
        margin-right: 5px;
        display: flex;
        border: 2px solid rgb(231, 222, 222);
        padding: 5px;
        width: 80px;
        border-radius: 30px;
        justify-content: center;
        font-size: 14px;
        color: rgb(231, 222, 222);
        input {
          color: black;
          padding-left: 5px;
          width: fit-content;
          width: 30px;
          background-color: transparent;
          outline: none;
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

.pledecardselect {
  .ContentMain {
    .textContent {
      .title-container {
        .title {
          .title-name:hover {
            cursor: url("data:image/x-icon;base64,AAACAAEAICACAAAAAAAwAQAAFgAAACgAAAAgAAAAQAAAAAEAAQAAAAAAgAAAAAAAAAAAAAAAAgAAAAAAAAAAAAAA////AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/gAAAf4AAAPVAAAH1QAAB9WAAA3VgAAd/4AAGbaAAAG2gAABtgAAAYAAAAGAAAABgAAAAYAAAAAAAAA//////////////////////////////////////////////////////////////////////////////////////gD///4A///8AP//+AB///AAf//wAD//4AA//8AAP//AAD//5AA///wAf//8Af///D////w////8P////n///8="),
              auto;
            color: rgb(21, 182, 171);
          }
        }
      }
    }
  }
}

.zero-days {
  opacity: 0.5;
  pointer-events: none;
}
.select-card {
  border-color: rgb(21, 182, 171) !important;
}
</style>
