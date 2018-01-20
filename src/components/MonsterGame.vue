<template>
    <div class="wrapper">
        <section class="row">
        <div class="small-6 columns">
            <h1 class="text-center">YOU</h1>
            <div class="healthbar">
                <div class="healthbar __lvl text-center" :style="humanWidth">
                    {{ humanHealth }}
                </div>
            </div>
        </div>
        <div class="small-6 columns">
            <h1 class="text-center">MONSTER</h1>
            <div class="healthbar">
                <div class="healthbar __lvl text-center" :style="monsterWidth">
                    {{ monsterHealth }}
                </div>
            </div>
        </div>
    </section>
    <section class="row controls" v-if="!controls">
        <div class="small-12 columns">
            <button id="start-game" @click.prevent="controls = !controls">START NEW GAME</button>
        </div>
    </section>
    <section class="row controls" v-if="controls">
        <div class="small-12 columns">
            <button id="attack" @click="attack">ATTACK</button>
            <button id="special-attack" @click="spattack">SPECIAL ATTACK</button>
            <button id="heal" @click="heal">HEAL</button>
            <button id="give-up" @click="giveup">GIVE UP</button>
        </div>
    </section>
    <section class="row log" v-if="log.length > 0">
        <div class="small-12 columns">
            <ul>
                <li v-for="action in log"
                    :class="{'player-turn': action.isPlayer, 'monster-turn': action.isMonster}"
                    >
                    {{ action.text }}
                </li>
            </ul>
        </div>
    </section>
    </div>
</template>

<script>

    export default {
        data() {
            return {
                controls: false,
                monsterHealth: 100,
                humanHealth: 100,
                log: []
            }
        },
        computed: {
            monsterWidth() {
                if (this.finishGame()) this.resetGame();
                return {width: this.monsterHealth + '%'};
            },
            humanWidth() {
                if (this.finishGame()) this.resetGame();
                return {width: this.humanHealth + '%'};
            }
        },
        methods: {
            getRandom(min, max) {
                return Math.floor(min + Math.random() * (max + 1 - min));
            },
            _move(min, max, target, increment) {
                const randomNum = this.getRandom(10, 20);
                if (increment) {
                    this[target] += randomNum;
                } else {
                    this[target] -= randomNum;
                    this.logFunc(target, randomNum);
                };
                if (!this.finishGame()) setTimeout(this.monster, 200);
            },
            _move2(min, max, target) {
                const randomNum = this.getRandom(10, 20);
                this[target] -= randomNum;
                this.logFunc(target, randomNum);
            },
            attack(min, max) {
                this._move(10, 20, 'monsterHealth', false);
            },
            spattack() {
                this._move(20, 40, 'monsterHealth', false);
            },
            heal() {
                this._move(10, 30, 'humanHealth', true);
            },
            monster() {
                this._move2(5, 10, 'humanHealth', false);
            },
            giveup() {
                if (confirm('Are you sure')) this.resetGame();
            },
            finishGame() {
                if (this.humanHealth < 0 || this.monsterHealth < 0) return true;
            },
            resetGame() {
                this.monsterHealth = this.humanHealth = 100;
                this.log = [];
            },
            logFunc(target, randomNum) {
                const monster = `monster hits human for ${ randomNum }`;
                const human = `human hits monster for ${ randomNum }`;
                
                if (target === 'monsterHealth') {
                    this.log.unshift({
                        isPlayer: true,
                        text: human
                    });
                } else {
                    this.log.unshift({
                        isMonster: true,
                        text: monster
                    });
                }
            }
        }
    }
</script>

<style src="../assets/foundation.min.css" scoped></style>

<style scoped>
.wrapper {
    margin-bottom: 20px;
}

.text-center {
    text-align: center;
}

.healthbar {
    width: 80%;
    height: 40px;
    background-color: #eee;
    margin: auto;
    transition: width 500ms;
}

.__lvl {
    background-color: green;
    margin: 0;
    color: white;
}

.controls, .log {
    margin-top: 30px;
    text-align: center;
    padding: 10px;
    border: 1px solid #ccc;
    box-shadow: 0px 3px 6px #ccc;
}

.turn {
    margin-top: 20px;
    margin-bottom: 20px;
    font-weight: bold;
    font-size: 22px;
}

.log ul {
    list-style: none;
    font-weight: bold;
    text-transform: uppercase;
}

.log ul li {
    margin: 5px;
}

.log ul .player-turn {
    color: blue;
    background-color: #e4e8ff;
}

.log ul .monster-turn {
    color: red;
    background-color: #ffc0c1;
}

button {
    font-size: 20px;
    background-color: #eee;
    padding: 12px;
    box-shadow: 0 1px 1px black;
    margin: 10px;
}

#start-game {
    background-color: #aaffb0;
}

#start-game:hover {
    background-color: #76ff7e;
}

#attack {
    background-color: #ff7367;
}

#attack:hover {
    background-color: #ff3f43;
}

#special-attack {
    background-color: #ffaf4f;
}

#special-attack:hover {
    background-color: #ff9a2b;
}

#heal {
    background-color: #aaffb0;
}

#heal:hover {
    background-color: #76ff7e;
}

#give-up {
    background-color: #ffffff;
}

#give-up:hover {
    background-color: #c7c7c7;
}
</style>