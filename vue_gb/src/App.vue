<template>
  <div>
    Hello, {{ name }}
    <br /> <br />

    <input type="text" v-model="name">
    <br /> <br />

    <img v-if="name === 'vue'" src="./assets/logo.png" alt="logo">
    <br /> <br />

    <ul>
        <li v-for="item, i of list" v-bind:key="i"><strong>{{ item.name}} </strong><span>{{ item.lastname}}</span></li>
    </ul>

    <button v-on:click="onShowModalBtnClick">Показать</button>
    <div v-if="isModalShowed" class="modal">
        <h2>Модальное окно</h2>
        <div class="rect" v-bind:style="`width:${rect.x}px; height:${rect.y}px`"> 
        </div>
        <h3>{{  square }}px</h3>
        <input type="text" v-model="rect.x" />
        <br /> <br />
        <input type="text" v-model="rect.y" />
        <br /> <br />
        <button v-on:click="onCloseModalBtnClick">Закрыть</button>
    </div>
    <br /> <br />



  </div>
</template>

<script>
export default {
    data() {
        return {
            name: "admin",
            isModalShowed: false,
            list: [
                {name: "John", lastname: "Doe"},
                {name: "Jane", lastname: "Doe"},
                {name: "John", lastname: "Smith"}
            ],
            rect: {x: 10, y: 15}
        }
    },
    computed: {
        square() {
            return this.rect.x * this.rect.y
        }
    },

    methods: {
        onShowModalBtnClick() {
            this.isModalShowed = true;
        },
        onCloseModalBtnClick() {
            this.isModalShowed = false;
        },
    },
    mounted() { 
    this.name = 'GeekBrains';
    },
}
</script>

<style lang="scss">

.modal {
    width: 1000px;
    height: 500px;
    background: #fff;
    border: 1px solid black;
    padding: 20px;
    border-radius: 10px;
    position: absolute;
    top: 100px;
    left: calc(50% - 500px);
}

.rect {
    border: 2px solid red;
    margin: 30px auto;
}

</style>
