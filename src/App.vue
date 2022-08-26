<script setup>
import { ref } from 'vue'

let star = ref(0);
let title = ref("How did we do?")
let paragraph = ref("Please let us know how we did with your support request. All feedback is appreciated to help us improve our offering!")
let aligns = ref("unset");
let textA = ref("unset");



function thanks() {
    title.value = "Thank you!";
    paragraph.value = "We appreciate you taking the time to give a rating. If you ever need more support, don’t hesitate to get in touch!"
    aligns = "center";
    textA = "center";


}

</script>
<template >
    <figure class="rating__icon" v-if="title !== 'Thank you!'">
        <img src="../images/icon-star.svg" alt="">
    </figure>

    <div class="rating__text">
        <figure v-show="title === 'Thank you!'" class="rating__thanks">
            <img src="../images/illustration-thank-you.svg" alt="">
        </figure>
        <p class="rating__num" v-show="title === 'Thank you!'">You selected {{ star }} out of 5</p>
        <h1 class="rating__title">{{ title }}</h1>
        <p class="rating__paragraph">{{ paragraph }}</p>
    </div>

    <form action="" class="rating__score" v-show="title !== 'Thank you!'">
        <div>
            <input type="radio" name="number" id="n0" class="radio">

            <input type="radio" name="number" id="n1" class="radio">
            <label @click="star = 1" class="rating__btn" for="n1">1</label>

            <input type="radio" name="number" id="n2" class="radio">
            <label @click="star = 2" class="rating__btn" for="n2">2</label>

            <input type="radio" name="number" id="n3" class="radio">
            <label @click="star = 3" class="rating__btn" for="n3">3</label>

            <input type="radio" name="number" id="n4" class="radio">
            <label @click="star = 4" class="rating__btn" for="n4">4</label>

            <input type="radio" name="number" id="n5" class="radio">
            <label @click="star = 5" class="rating__btn" for="n5">5</label>
        </div>

        <input :disabled="star === 0" @click="thanks" class="rating__sub" type="button" value="submit">

    </form>

</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Overpass:wght@400;700&display=swap');

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    text-decoration: none;
}

$Font: 'Overpass', sans-serif;
$Orange: hsl(25, 97%, 53%);
$White: hsl(0, 0%, 100%);
$Light-Grey: hsl(217, 12%, 63%);
$Medium-Grey: hsl(216, 12%, 54%);
$Dark-Blue: hsl(213, 19%, 18%);
$Very-Dark-Blue: hsl(216, 12%, 8%);

body,
html {
    min-height: 100vh;
    font-family: 'Overpass', sans-serif;
    font-size: 15px;
    color: $White;
}

body {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: $Very-Dark-Blue;

}

.radio {
    display: none;
}

#app {

    margin: 1rem;
    border-radius: 1rem;
    max-width: 450px;

    padding: 2rem;
    background-image: linear-gradient(#272e38, #171e28 30%);
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: clamp(1rem, 5vw, 3rem);


}


.rating {
    &__icon {
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 1rem;
        background-color: #272e38;
        width: 50px;
        aspect-ratio: 1;
        border-radius: 50%;
    }

    &__num {
        padding: .5rem;
        background-color: #272e38;
        color: $Orange;
        border-radius: 100vmax;


    }

    &__text {
        display: flex;
        justify-content: center;
        align-items: v-bind(aligns);
        flex-direction: column;
        gap: 2rem;
    }

    &__score div {
        display: flex;
        justify-content: space-between;
        align-items: center;


    }

    &__score {
        display: flex;
        flex-direction: column;
        gap: 2rem;
    }

    &__paragraph {
        color: $Light-Grey;
        text-align: v-bind(textA);
    }

    &__btn {
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
        transition: all .3s;
        background-color: #272e38;
        border-radius: 50%;
        aspect-ratio: 1;
        color: $Light-Grey;
        font-weight: bold;
        width: clamp(40px, 10vw, 50px);
        text-align: center;

        &:hover {
            color: $White;
            background-color: $Medium-Grey;
        }



    }

    &__sub {
        transition: all .3s;
        font-family: $Font;
        font-weight: bold;
        cursor: pointer;
        border: none;
        width: 100%;
        border-radius: 100vmax;
        background-color: $Orange;
        text-transform: uppercase;
        letter-spacing: 3px;

        color: $White;
        font-size: 1.3rem;
        padding: 1rem;

        &:disabled {
            opacity: .5;
        }

        &:hover {
            background-color: $White;
            color: $Orange;
        }
    }
}

.radio:checked+.rating__btn {
    background-color: $Orange;
    color: $White;

}
</style>