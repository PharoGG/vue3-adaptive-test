<template>
  <div class="container">
    <div class="header">
      <h1>Invictus</h1>
      <h3>By William Ernest Henley</h3>
    </div>

    <div class="content">
      <div class="controls">
        <label
          v-for="(quatrain, index) in quatrains"
          :key="index"
          class="control"
        >
          <div
            class="square"
            :class="{ active: quatrain.visible }"
            @click="toggleVisibility(index)"
          ></div>
        </label>
      </div>

      <div class="poem">
        <QuatrainText
          v-for="(quatrain, index) in quatrains"
          :key="index"
          :text="quatrain.text"
          :visible="quatrain.visible"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import QuatrainText from "./components/QuatrainText.vue";

const quatrains = ref([
  {
    text: "Out of the night that covers me,\n\tBlack as the pit from pole to pole,\nI thank whatever gods may be\n\tFor my unconquerable soul.",
    visible: true,
  },
  {
    text: "In the fell clutch of circumstance\n\tI have not winced nor cried aloud.\nUnder the bludgeonings of chance\n\tMy head is bloody, but unbowed.",
    visible: true,
  },
  {
    text: "Beyond this place of wrath and tears\n\tLooms but the Horror of the shade,\nAnd yet the menace of the years\n\tFinds and shall find me unafraid.",
    visible: true,
  },
  {
    text: "It matters not how strait the gate,\n\tHow charged with punishments the scroll,\nI am the master of my fate,\n\tI am the captain of my soul.",
    visible: true,
  },
]);

function toggleVisibility(index) {
  if (
    quatrains.value.filter((q) => q.visible).length > 1 ||
    !quatrains.value[index].visible
  ) {
    quatrains.value[index].visible = !quatrains.value[index].visible;
  }
}
</script>

<style scoped>
.container {
  max-width: 850px;
  margin: 0 auto;
  padding: 20px;
}

.header {
  margin-left: 260px;
  display: flex;
  justify-content: space-between;
  align-items: baseline;
}

h1 {
  padding-left: 8rem;
  font-size: 2rem;
  margin: 0;
}

h3 {
  font-size: 1.2rem;
  margin: 0;
}

.content {
  display: flex;
}

.controls {
  display: flex;
  flex-direction: row;
  margin-right: 10px;
  margin-top: 20px;
}

.control {
  margin-right: 5px;
}

.square {
  width: 20px;
  height: 20px;
  background-color: white;
  border: 2px solid black;
  cursor: pointer;
  margin-right: 20px;
  margin-top: 12px;
}

.square.active {
  background-color: black;
}

.poem {
  font-family: "Georgia", serif;
  white-space: pre-wrap;
  text-align: left;
  margin-left: 10px;
}

/* Адаптивные стили для мобильных устройств */
@media (max-width: 768px) {
  .container {
    max-width: 100%;
    padding: 10px;
  }

  .header {
    margin-left: 0;
    flex-direction: column;
    align-items: center;
  }

  h1 {
    font-size: 1.5rem;
    padding-left: 0;
  }

  h3 {
    font-size: 1rem;
    margin-top: 0.5rem;
  }

  .content {
    flex-direction: column;
    align-items: center;
  }

  .controls {
    margin: 0 auto 20px auto;
    padding-left: 25px;
  }

  .square {
    width: 16px;
    height: 16px;
    margin-top: 8px;
  }

  .poem {
    padding-left: 3rem;
    text-align: left;
    margin-left: 0;
  }
}

/* Адаптивные стили для больших экранов */
@media (min-width: 2560px) {
  .container {
    max-width: 1150px;
    padding: 30px;
  }

  h1 {
    font-size: 2.8rem;
    padding-left: 16.3rem;
  }

  h3 {
    font-size: 1.6rem;
  }

  .controls {
    padding-top: 15px;
  }

  .square {
    width: 30px;
    height: 30px;
    margin-right: 30px;
  }
}

@media (min-width: 3840px) {
  .container {
    max-width: 1550px;
    padding: 50px;
  }

  h1 {
    font-size: 4.2rem;
    padding-left: 27rem;
  }

  h3 {
    font-size: 2.2rem;
  }

  .controls {
    padding-top: 35px;
  }

  .square {
    width: 43px;
    height: 43px;
    margin-right: 43px;
  }
}

@media (min-width: 7680px) {
  .container {
    max-width: 3100px;
    padding: 100px;
  }

  h1 {
    font-size: 9rem;
    padding-left: 68rem;
  }
  h3 {
    font-size: 4.5rem;
  }

  .controls {
    padding-top: 90px;
  }

  .square {
    width: 90px;
    height: 90px;
    margin-right: 90px;
  }
}
</style>
