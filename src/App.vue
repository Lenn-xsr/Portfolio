<template>
  <div id="app">
    <transition mode="out-in">
      <router-view />
    </transition>
    <Aside />
  </div>
</template>
<script>
import Aside from "@/components/Basics/Aside.vue";

export default {
  components: {
    Aside,
  },
};
</script>

<style>
::-webkit-scrollbar {
  width: 2px;
  height: 2px;
}

::-webkit-scrollbar-button {
  width: 0px;
  height: 0px;
}

::-webkit-scrollbar-thumb {
  background: var(--lighted);
  border: 0px none var(--lighted);
  border-radius: 50px;
}

::-webkit-scrollbar-thumb:hover {
  background: #ffffff;
}

::-webkit-scrollbar-thumb:active {
  background: var(--activated);
}

::-webkit-scrollbar-track {
  background: transparent;
  border: 0px none var(--lighted);
  border-radius: 50px;
}

::-webkit-scrollbar-track:hover {
  background: var(--activated);
}

::-webkit-scrollbar-track:active {
  background: transparent;
}

::-webkit-scrollbar-corner {
  background: transparent;
}

* {
  box-sizing: border-box;
  font-family: "Noto Sans", sans-serif;
}

body,
html {
  color: var(--secondary);
  background: var(--primary);
  font-size: initial;
  line-height: initial;
}

::after,
::before {
  box-sizing: content-box;
}

:root {
  --primary: #111111;
  --secondary: #f7f0f0;
  --secondary-fading: #aaa9a9;
  --tertiary: #fd7624;
  --fading: #43434491;
  --lighted: #353ffb;
  --lighted-fading: #353ffbcc;
  --default-shadow: 0 4px 3px 0 rgba(255, 255, 255, 0.4);
}

#app {
  display: flex;
  min-height: 100vh;
}

.lock-width {
  max-width: 1120px;
}

main {
  flex: 1;
  max-height: 100vh;
  overflow-y: auto;
  scrollbar-width: thin;
  scrollbar-color: transparent transparent;
}

body,
ul,
li,
h1,
h2,
p {
  padding: 0px;
  margin: 0px;
  font-weight: revert;
  line-height: normal;
  color: inherit;
}

h2 {
  font-size: 22px;
}

ul {
  list-style: none;
}

a {
  text-decoration: none;
  color: var(--secondary);
}

a:focus,
a:hover {
  text-decoration: none;
}

p {
  color: var(--secondary-fading);
  font-size: 0.9rem;
  line-height: 1.7;
  white-space: break-spaces;
}

img {
  display: block;
  max-width: 100%;
}

input,
textarea,
select {
  background-color: var(--secondary);
  color: var(--text-secondary);
  border: 1px solid #c4c4c4;
  padding: 6.4px;
  border-radius: 5px;
}

textarea {
  resize: vertical;
}

.mini-icon {
  z-index: 2;
  background-color: var(--text-secondary);
  padding: 8px;
  border-radius: 7px;
  font-size: smaller;
  display: grid;
  place-content: center;
  position: relative;
  cursor: pointer;
}

.icon-grab {
  cursor: grab;
}

.mini-icon:hover {
  background-color: var(--lighted-secondary);
}

.switch {
  position: relative;
  display: inline-block;
  width: 40px;
  height: 22px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: var(--activated);
  border-radius: 34px;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider::before {
  position: absolute;
  content: "";
  height: 14px;
  width: 14px;
  left: 4px;
  bottom: 4px;
  border-radius: 50%;
  background-color: var(--secondary);
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: var(--lighted-secondary);
}

input:focus + .slider {
  box-shadow: 0 0 1px #2196f3;
}

input:checked + .slider::before {
  -webkit-transform: translateX(20px);
  -ms-transform: translateX(20px);
  transform: translateX(20px);
}

.router-link-exact-active,
.router-link:hover,
.router-link:focus {
  color: var(--activated);
}

.v-enter,
.v-leave-to {
  opacity: 0;
}

.v-enter {
  transform: translate3d(-100%, 0, 0);
}

.v-leave {
  transform: translate3d(0, 0, 0);
}

.v-enter-active,
.v-leave-active {
  transition: all 0.3s;
}

/* Animation Keyframes */

@keyframes slide-from-left {
  0% {
    opacity: 0;
    transform: translate3d(-100%, 0, 0);
  }
  100% {
    transform: translate3d(0, 0, 0);
  }
}

@keyframes slide-from-right {
  0% {
    opacity: 0;
    transform: translate3d(100%, 0, 0);
  }
  100% {
    transform: translate3d(0, 0, 0);
  }
}

@keyframes dashed-anim {
  0% {
    max-height: 0;
  }
  100% {
    max-height: 100%;
  }
}

@keyframes slide-from-bottom {
  0% {
    opacity: 0;
    transform: translate3d(0, 25px, 0);
  }
  100% {
    transform: translate3d(0, 0, 0);
  }
}

@keyframes project-from-bottom {
  0% {
    opacity: 0;
    transform: translate3d(0, 40vw, 0);
  }
  100% {
    transform: translate3d(0, 0, 0);
  }
}

@keyframes menu-from-left {
  0% {
    transform: translate3d(-200%, 0, 0);
  }
  100% {
    transform: translate3d(0, 0, 0);
  }
}

@keyframes width-animation {
  0% {
    width: 0%;
  }
  100% {
    width: 100%;
  }
}
</style>
