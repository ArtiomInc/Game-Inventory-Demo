<script setup>
import { ref } from 'vue';

let moving1 = false;
let moving2 = false;
let offsetComponent1X = ref(30);
let offsetComponent1Y = ref(30);
let offsetMouseClient1X = 0;
let offsetMouseClient1Y = 0;
let offsetComponent2X = ref(360);
let offsetComponent2Y = ref(30);
let offsetMouseClient2X = 0;
let offsetMouseClient2Y = 0;

const startMove1 = (event) => {
  moving1 = true;
  offsetMouseClient1X = event.clientX - offsetComponent1X.value;
  offsetMouseClient1Y = event.clientY - offsetComponent1Y.value;
};

const startMove2 = (event) => {
  moving2 = true;
  offsetMouseClient2X = event.clientX - offsetComponent2X.value;
  offsetMouseClient2Y = event.clientY - offsetComponent2Y.value;
};

const handleMove = (event) => {
  if (moving1) {
    offsetComponent1X.value = event.clientX - offsetMouseClient1X;
    offsetComponent1Y.value = event.clientY - offsetMouseClient1Y;
  }
  if (moving2) {
    offsetComponent2X.value = event.clientX - offsetMouseClient2X;
    offsetComponent2Y.value = event.clientY - offsetMouseClient2Y;
  }
};

const stopMove = () => {
  moving1 = false;
  moving2 = false;
};

const drag = (event) => {
  event.dataTransfer.setData('text', event.target.id);
};

const allowDrop = (event) => {
  event.preventDefault();
};

const drop = (event) => {
  event.preventDefault();
  var data = event.dataTransfer.getData('text');
  event.target.appendChild(document.getElementById(data));
};
</script>

<template>
  <div
    class="relative h-screen w-screen"
    @mouseup="stopMove"
    @mousemove="handleMove"
  >
    <div
      class="absolute w-[300px]"
      :style="{ top: offsetComponent1Y + 'px', left: offsetComponent1X + 'px' }"
    >
      <div class="header" @mousedown="startMove1"></div>
      <div class="container">
        <div
          id="a11"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        >
          <img
            id="CPU_Fan"
            src="./assets/CPU_Fan_Icon.webp"
            draggable="true"
            @dragstart="drag"
          />
        </div>
        <div
          id="a12"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        >
          <img
            id="ElectronicComponents"
            src="./assets/ElectronicComponents_icon.webp"
            draggable="true"
            @dragstart="drag"
          />
        </div>
        <div
          id="a13"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        >
          <img
            id="Energy-Saving_Lamp"
            src="./assets/Energy-Saving_Lamp_Icon.webp"
            draggable="true"
            @dragstart="drag"
          />
        </div>
        <div
          id="b11"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
        <div
          id="b12"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
        <div
          id="b13"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
        <div
          id="c11"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
        <div
          id="c12"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
        <div
          id="c13"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
      </div>
    </div>
    <div
      class="absolute w-[300px]"
      :style="{ top: offsetComponent2Y + 'px', left: offsetComponent2X + 'px' }"
    >
      <div class="header" @mousedown="startMove2"></div>
      <div class="container">
        <div
          id="a21"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
        <div
          id="a22"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
        <div
          id="a23"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
        <div
          id="b21"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
        <div
          id="b22"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
        <div
          id="b23"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
        <div
          id="c21"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
        <div
          id="c22"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
        <div
          id="c23"
          class="item"
          @dragover.prevent
          @drop="drop"
          @ondragover="allowDrop"
        ></div>
      </div>
    </div>
  </div>
</template>

<style>
.header {
  background: rgb(0, 0, 0);
  background: linear-gradient(
    0deg,
    rgba(50, 50, 50, 1) 0%,
    rgba(255, 255, 255, 0.3) 100%
  );
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-bottom: 0;
  height: 20px;
  width: 100%;
}
.container {
  background: rgba(255, 255, 255, 0.1);
  display: grid;
  grid-template-columns: 100px 100px 100px;
  grid-template-rows: 100px 100px 100px;
  gap: 0px 0px;
  grid-auto-flow: row;
  grid-template-areas:
    'a1 a2 a3'
    'b1 b2 b3'
    'c1 c2 c3';
}

#a1 {
  grid-area: a1;
}

#a2 {
  grid-area: a2;
}

#a3 {
  grid-area: a3;
}

#b1 {
  grid-area: b1;
}

#b2 {
  grid-area: b2;
}

#b3 {
  grid-area: b3;
}

#c1 {
  grid-area: c1;
}

#c2 {
  grid-area: c2;
}

#c3 {
  grid-area: c3;
}
.item {
  border: 1px solid rgba(255, 255, 255, 0.2);
  display: flex;
  justify-content: center;
  align-items: center;
}
.item img {
  height: 100%;
  width: 100%;
  user-select: none;
}
.item:hover:has(img) {
  background-color: rgba(255, 255, 255, 0.1);
  cursor: pointer;
}
</style>
