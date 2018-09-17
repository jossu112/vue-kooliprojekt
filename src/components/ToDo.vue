<template>
    <div>
        <input type="text" v-model="uusAsi.kirjeldus"><button @click="lisaAsi()">Lisa asi</button>
        <div class="tegemataKonteiner">
            <span>TEGEMATA ASJAD</span>
            <div></div>
            <ul>
                <li class="tegemata" v-for="(asi, index) in tegemataAsjad" :key="index">
                    {{asi.kirjeldus}}<br/><button @click="asiTehtud({asi: asi, index: index})">Asi tehtud!</button>
                </li>
            </ul>
        </div>
        <div class="tehtudKonteiner">
            <span>TEHTUD ASJAD</span>
            <ul>
                <li class="tehtud" v-for="(asi, index) in tehtudAsjad" :key="index">
                    {{index}}-{{asi.kirjeldus}}
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
  name: 'ToDo',
  data: function () {
    return {
      uusAsi: {},
      tegemataAsjad: [],
      tehtudAsjad: []
    }
  },
  methods: {
    lisaAsi: function () {
      this.tegemataAsjad.push(Object.assign({}, this.uusAsi))
    },
    asiTehtud: function (payload) {
      this.tehtudAsjad.push(Object.assign({}, payload.asi))
      this.tegemataAsjad.splice(payload.index, 1)
    }
  }
}
</script>

<style scoped>

    .tehtud {
        background-color: limegreen;
        text-decoration: line-through;
        border: 1px solid grey;
        border-radius: 8px;
        margin: auto;
        position: relative;
    }

    .tegemata {
        background-color: crimson;
        border: 1px solid grey;
        justify-content: center;
        border-radius: 8px;
        margin: auto;
        position: relative;
    }

    .tehtudKonteiner {
        height: 300px;
        width: 300px;
        background-color: #aaff80;
        justify-content: center;
        align-items: center;
        border: 1px solid green;
        border-radius: 8px;
        display: flex;
        margin: 0 auto;
        overflow-y: scroll;
        position: relative;
    }

    .tehtudKonteiner span, .tegemataKonteiner span {
        display: flex;
        word-wrap: break-word;
        height: 30px;
        top: 20px;
        position: absolute;
    }

    .tegemataKonteiner {
        height: 300px;
        width: 300px;
        background-color: #ff6666;
        justify-content: center;
        align-items: center;
        border: 1px solid red;
        border-radius: 8px;
        display: flex;
        margin: 0 auto;
        overflow-y: scroll;
        position: relative;
    }

</style>
