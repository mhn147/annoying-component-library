<template>
    <button class="annoying-button" @click="onClick"
        :style="{ height: buttonHeight, width: buttonWidth, fontSize: buttonFontSize }">
        {{text}}
    </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name: "AnnoyingButton",
    data() {
        return {
            text: "CLICK ME!",
            height: 75,
            width: 150,
            fontSize: 1,
            intervalHandle: 0 as number,
        };
    },
    computed: {
        buttonHeight() {
            return `${this.height}px`;
        },
        buttonWidth() {
            return `${this.width}px`;
        },
        buttonFontSize() {
            return `${this.fontSize}rem`;
        },
    },
    methods: {
        onClick() {
            alert("I'm an annoying button!");
            this.width = 150;
            this.height = 75;
            this.fontSize = 1;
            this.text = "CLICK ME!";
        },
    },
    mounted() {
        this.intervalHandle = window.setInterval(() => {
            this.width = this.width * 1.1;
            this.height = this.height * 1.1;
            this.fontSize = this.fontSize * 1.1;
            this.text += "!";
        }, 1000);
    },
});
</script>

<style scoped>
.annoying-button {
    display: inline-block;
    padding: 1rem;
    font-size: 1.2rem;
}
</style>
