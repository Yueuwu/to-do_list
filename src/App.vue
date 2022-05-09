<template>
    <div id="app" class="container">
        <div class="card">
            <div class="top">
                <div class="forH1"><h1>{{title}}</h1></div>
                <div class="forCount">Number of notes: {{ notes.length }} </div>
            </div>

            <div class="form-control">
                <input
                    v-bind:value="inputValue"
                    v-bind:placeholder="placeHold"
                    v-on:input="inputChangeHandler"
                    v-on:keypress.enter="addNewNote"
                    type="text" class="text">
                <!-- <h2>Input Value: {{ inputValue }} </h2> -->
            </div>
            <button class="btn " v-on:click="addNewNote">Add</button>
<!--            <button id="scrollEnd" class="scroll">To end</button>-->
            <hr>
            <ul class="list" v-if="notes.length !== 0">
                <li class="list-item" v-for="(myNote, index) in notes" :key="myNote">{{ myNote }}
                    <button id="el" class="btn danger" v-on:click="removeN(index)">Delete note</button>
                </li>
            </ul>
            <div class="oldrem">
                <button id="element" class="rem" v-on:click="removeAll">Remove all</button>
<!--                <button id="scrollTop" class="start rem">To start</button>-->

                <div class="pumpin">
                    <input
                        v-bind:value="pumpNote"
                        v-on:input="inputChangeVal"
                        v-on:keypress.enter="addSomeNote"
                        placeholder="Enter number"
                        type="number"
                        class="pumpNumb ">
                    <button v-on:click="addSomeNote" class="pump btn">Pump</button>

                </div>


    </div>
        </div>
        <el-backtop :bottom="100">
            <div
                style="
        height: 100%;
        width: 100%;
        border-radius: 15%;
        background-color: #42b983;
        box-shadow: #3eaf7c;
        text-align: center;
        line-height: 40px;
        color: #fff;
      "
            >
                UP
            </div>
        </el-backtop>
        <!-- <h1>{{ title }}: {{ counter + 1 }}</h1>
        <div class="">
           <button class="btn  primary" v-on:click="counter++">+</button>
           <button class="btn  danger" v-on:click="counter--">-</button>
       </div>  -->
    </div>
</template>

<script>
export default {
        data(){
            return {
                counter: -1,
                title: 'List notions',
                placeHold: 'Enter some text',
                inputValue: '',
                pumpNote: NaN,
                notes: ['Note 1', 'Note 2'],
            }
        },
        methods: {
            inputChangeHandler(event) {
                this.inputValue = event.target.value;
            },
            addNewNote() {
                this.notes.push(this.inputValue);
                this.inputValue = '';
            },
            removeN(index){
                this.notes.splice(index, 1);
            },
            removeAll(){
                this.notes.splice(0, this.notes.length);
            },
            inputChangeVal(event){
                this.pumpNote = event.target.value;
            },
            addSomeNote() {
                for(let i = 0; i < this.pumpNote; i++)
                {
                    this.notes.push(this.inputValue);
                }
                this.pumpNote = NaN;
            }
        },

//скролл
//     document.addEventListener('DOMContentLoaded', () => {
//         document.querySelector('#scrollEnd').addEventListener('click', () => {
//             document.querySelector('.rem').scrollIntoView({
//                 block: 'center',
//                 behavior: 'smooth',
//             });
//         })})
//     document.addEventListener('DOMContentLoaded', () => {
//         document.querySelector('#scrollTop').addEventListener('click', () => {
//             document.querySelector('.top').scrollIntoView({
//                 block: 'center',
//                 behavior: 'smooth',
//             });
//         })})
}
</script>

<style>
* {
    padding: 0;
    margin: 0;
    border: 0;
}

*, *:before, *:after {
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
}

:focus, :active {
    outline: none;
}

a:focus, a:active {
    outline: none;
}

nav, footer, header, aside {
    display: block;
}

html, body {
    height: 100%;
    width: 100%;
    font-size: 100%;
    line-height: 1;
    font-size: 14px;
    -ms-text-size-adjust: 100%;
    -moz-text-size-adjust: 100%;
    -webkit-text-size-adjust: 100%;
}

input, button, textarea {
    font-family: inherit;
}

input::-ms-clear {
    display: none;
}

button {
    cursor: pointer;
}

button::-moz-focus-inner {
    padding: 0;
    border: 0;
}

a, a:visited {
    text-decoration: none;
}

a:hover {
    text-decoration: none;
}

ul li {
    list-style: none;
}

img {
    vertical-align: top;
}

h1, h2, h3, h4, h5, h6 {
    font-size: inherit;
    font-weight: inherit;
}

/*--------------------*/
.container {
    padding: 30px;
}

* {
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
}

body {
    font-family: Inter, Roboto, Oxygen, Fira Sans, Helvetica Neue, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-size: 170%;
    color: #2c3e50;
    background: #2c3e50;
    height: 1000px;
}

.oldrem {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    display: flex;
    -webkit-box-orient: horizontal;
    -webkit-box-direction: normal;
    -ms-flex-direction: row;
    flex-direction: row;
    width: 100%;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    -webkit-box-pack: start;
    -ms-flex-pack: start;
    justify-content: start;
}

.top {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: horizontal;
    -webkit-box-direction: normal;
    -ms-flex-direction: row;
    flex-direction: row;
    width: 100%;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    -ms-flex-pack: distribute;
    justify-content: space-around;
    margin-bottom: 2%;
}

.forH1 {
    -webkit-box-shadow: 1em -5px 5px rgba(243, 235, 9, 0.536), -1em 0.2em 0.4em rgba(122, 209, 102, 0.722);
    box-shadow: 1em -5px 5px rgba(243, 235, 9, 0.536), -1em 0.2em 0.4em rgba(122, 209, 102, 0.722);
    background: rgba(17, 198, 214, 0.293);
}

.pumpin {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: horizontal;
    -webkit-box-direction: normal;
    -ms-flex-direction: row;
    flex-direction: row;
    width: 33%;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    -webkit-box-pack: start;
    -ms-flex-pack: start;
    justify-content: start;
}

.scroll {
    color: #42b983;
    position: relative;
    border-radius: 99px;
    letter-spacing: 0.05em;
    border: 1px solid #42b983;
    text-transform: uppercase;
    padding: 0.5rem 1.5rem;
    white-space: nowrap;
    font-weight: 700;
    outline: none;
    background: #fff;
}

.start {
    margin-top: 10px;
    margin-right: 4%;
}

.pumpNumb {
    color: #42b983;
    position: relative;
    place-content: center;
    place-items: center;
    width: -moz-fit-content;
    width: fit-content;
    border-radius: 99px;
    letter-spacing: 0.05em;
    border: 1px solid #42b983;
    text-decoration: none;
    text-transform: uppercase;
    margin-right: 3%;
    margin-top: 4%;
    padding: 0.5rem 1.5rem;
    white-space: nowrap;
    font-weight: 700;
    outline: none;
    background: #fff;
    -webkit-transition: all 0.22s;
    transition: all 0.22s;
}

.rem {
    color: #ffffff;
    position: relative;
    place-content: center;
    place-items: center;
    width: -moz-fit-content;
    width: fit-content;
    border-radius: 99px;
    letter-spacing: 0.05em;
    border: 1px solid #42b983;
    text-decoration: none;
    text-transform: uppercase;
    margin-right: 2%;
    margin-top: 1.5%;
    padding: 0.5rem 1.5rem;
    white-space: nowrap;
    font-weight: 700;
    outline: none;
    background: #42b983;
    -webkit-transition: all 0.22s;
    transition: all 0.22s;
}

hr {
    margin: 1rem 0;
}

strong,
.bold {
    font-weight: 500;
}

ol,
p,
ul {
    line-height: 1.7;
}

a {
    color: #3eaf7c;
    font-weight: 500;
    text-decoration: none;
}

h1,
h2,
h3,
h4,
h5,
h6 {
    font-weight: 500;
    line-height: 1.45;
}

h1 {
    font-size: 2.2rem;
    font-weight: 600;
}

h2 {
    font-size: 1.65rem;
    padding-bottom: 0.3rem;
    border-bottom: 1px solid #eaecef;
}

h3 {
    font-size: 1.35rem;
}

/*.primary {*/
/*    color: #42b983;*/
/*}*/
/*.danger {*/
/*    color: #e53935;*/
/*}*/
.btn {
    color: #42b983;
    position: relative;
    place-content: center;
    place-items: center;
    width: -moz-fit-content;
    width: fit-content;
    border-radius: 99px;
    letter-spacing: 0.05em;
    border: 1px solid #42b983;
    text-decoration: none;
    text-transform: uppercase;
    margin-right: 2%;
    margin-top: 10px;
    padding: 0.5rem 1.5rem;
    white-space: nowrap;
    font-weight: 700;
    outline: none;
    background: #fff;
    -webkit-transition: all 0.22s;
    transition: all 0.22s;
}

.btn:hover {
    cursor: pointer;
    opacity: 0.8;
}

.btn:disabled {
    cursor: not-allowed;
    opacity: 1 !important;
    background: #eee !important;
    border-color: #ddd !important;
    color: #999 !important;
}

.btn:active {
    -webkit-box-shadow: inset 1px 1px 1px rgba(0, 0, 0, 0.3);
    box-shadow: inset 1px 1px 1px rgba(0, 0, 0, 0.3);
}

.btn.primary {
    background: #42b983;
    color: #fff;
}

.btn.danger {
    background: #e53935;
    color: #fff;
    border-color: #e53935;
}

.btn.warning {
    background: #c25205;
    color: #fff;
    border-color: #c25205;
}

.container {
    margin: 0 auto;
    max-width: 1000px;
}

.container.with-nav {
    margin-top: 70px;
}

.pt-2 {
    padding-top: 2rem;
}

.pt-1 {
    padding-top: 1rem;
}

.pt-5 {
    padding-top: 5rem;
}

.form-control {
    position: relative;
    margin-bottom: 0.5rem;
}

.form-control input,
.form-control select {
    margin: 0;
    outline: none;
    border: 2px solid #ccc;
    display: block;
    width: 100%;
    color: #2c3e50;
    padding: 0.5rem 1.5rem;
    border-radius: 3px;
    font-size: 1rem;
}

.form-control small {
    color: #e53935;
}

.form-control.invalid input {
    border-color: #e53935;
}

.form-checkbox {
    margin-bottom: 1rem;
}

.form-checkbox .label {
    display: block;
    margin: 0 0 0.3rem 0.3rem;
    font-weight: 500;
}

.form-checkbox .checkbox input {
    margin-right: 1rem;
}

.form-control label {
    display: block;
    margin: 0 0 0.3rem 0.3rem;
    font-weight: 500;
}

.form-control input:active,
.form-control input:focus {
    -webkit-transition: border 0.22s;
    transition: border 0.22s;
    border: 2px solid #42b983;
}

.card {
    overflow: hidden;
    padding: 1rem;
    margin-bottom: 1rem;
    border-radius: 10px;
    -webkit-box-shadow: 2px 3px 10px rgba(0, 0, 0, 0.2);
    box-shadow: 2px 3px 10px rgba(0, 0, 0, 0.2);
    background: #fff;
}

.card.marked {
    border: 4px solid #42b983;
}

.card.center {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
    -ms-flex-direction: column;
    flex-direction: column;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
}

.list {
    margin: 0;
    padding: 0;
    list-style: none;
    background-color: #42b98334;
}

.list-item {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    -webkit-box-pack: justify;
    -ms-flex-pack: justify;
    justify-content: space-between;
    padding: 0.5rem 0;
    -webkit-transition: 0.22s all;
    transition: 0.22s all;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
}

.list-item:hover {
    background: #eee;
}

.alert {
    padding: 1rem 1.5rem;
    border-left-width: 0.5rem;
    border-left-style: solid;
    margin: 1rem 0;
    position: relative;
    border-bottom-right-radius: 2px;
    border-top-right-radius: 2px;
}

.alert.primary {
    border-color: #42b983;
    background-color: #f8f8f8;
}

.alert.danger {
    border-color: #e53935;
    background-color: #f8f8f8;
}

.alert.warning {
    border-color: #c25205;
    background-color: #f8f8f8;
}

.alert p {
    color: #222;
    line-height: 1.7;
}

.alert-title {
    text-transform: uppercase;
    font-weight: 600;
    margin-bottom: -0.4rem;
    color: #222;
}

.modal {
    position: fixed;
    top: 60px;
    width: 600px;
    padding: 1rem;
    background: #fff;
    z-index: 1000;
    left: 50%;
    border-radius: 10px;
    -webkit-transform: translateX(-50%);
    transform: translateX(-50%);
    -webkit-box-shadow: 2px 3px 10px rgba(0, 0, 0, 0.2);
    box-shadow: 2px 3px 10px rgba(0, 0, 0, 0.2);
}

.modal-backdrop {
    position: fixed;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.35);
}

.loader {
    font-size: 10px;
    margin: 50px auto;
    text-indent: -9999em;
    width: 11em;
    height: 11em;
    border-radius: 50%;
    background: #ffffff;
    background: -webkit-gradient(linear, left top, right top, color-stop(10%, #ffffff), color-stop(42%, rgba(255, 255, 255, 0)));
    background: linear-gradient(to right, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    position: relative;
    -webkit-animation: load3 1.4s infinite linear;
    animation: load3 1.4s infinite linear;
    -webkit-transform: translateZ(0);
    transform: translateZ(0);
}

.loader:before {
    width: 50%;
    height: 50%;
    background: #ffffff;
    border-radius: 100% 0 0 0;
    position: absolute;
    top: 0;
    left: 0;
    content: "";
}

.loader:after {
    background: #2c3e50;
    width: 75%;
    height: 75%;
    border-radius: 50%;
    content: "";
    margin: auto;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
}

@-webkit-keyframes load3 {
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(360deg);
        transform: rotate(360deg);
    }
}
@keyframes load3 {
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(360deg);
        transform: rotate(360deg);
    }
}
.navbar {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    padding: 0 2rem;
    -webkit-box-pack: justify;
    -ms-flex-pack: justify;
    justify-content: space-between;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    position: fixed;
    z-index: 20;
    top: 0;
    left: 0;
    right: 0;
    height: 56px;
    background-color: #fff;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    border-bottom: 1px solid #eaecef;
}

.navbar-menu {
    list-style: none;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
}

.navbar-menu li {
    margin-right: 2rem;
}

.navbar-menu li a {
    color: #2c3e50;
    text-decoration: none;
}

.navbar-menu li a:hover, .navbar-menu li a.active {
    border-bottom: 2px solid #3eaf7c;
}
</style>