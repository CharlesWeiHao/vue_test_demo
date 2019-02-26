<template>
    <div>
        <ul>
            <li v-for="(item, index) in list"
                :key="index"
                @click="choose(index)"
                :class="{active: index == currentIndex && currentIndex !== ''}"
            >{{item}}</li>
        </ul>

        <button type="button" @click="addClick()">add element</button>

        <ul>
            <li v-for="(item, index) in newList" :key="index"
            >
                {{ item }}
            </li>
        </ul>
    </div>

</template>

<script>
    export default {
        name: "demo",
        data () {
            return {
                list: [1,2,3,4,5,6,7,8,9,10],
                currentIndex: '',
                newList: [],
            }
        },
        methods: {
            choose(index) {
                console.log('index -', index);
                this.currentIndex = index;
            },

            addClick() {
                if (this.currentIndex === '') { return; }
                this.newList.push(this.list[this.currentIndex]);
                this.currentIndex = '';
            }
        }
    }
</script>

<style scoped>
li.active {
    background: green;
}
</style>
