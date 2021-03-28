<template>
  <div>
    <h1 class="title">@dafcoe/vue-swappable-card</h1>

    <div class="wrapper">
      <div class="dashboard--left">
        <div class="dashboard">
          <div class="dashboard__row">
            <span class="dashboard__row-label">Direction:</span>
            <span class="dashboard__row-content">
              <span
                v-for="swapDirection in ['from-top', 'from-right', 'from-bottom', 'from-left']"
                :key="swapDirection"
              >
                <input
                  v-model="direction"
                  :id="swapDirection"
                  :value="swapDirection"
                  type="radio"
                >
                <label :for="swapDirection">
                  {{ swapDirection }}
                </label>
              </span>
            </span>
          </div>

          <div class="dashboard__row">
            <span class="dashboard__row-label">Event:</span>
            <span>
              <span
                v-for="swapEvent in ['over', 'click']"
                :key="swapEvent"
                class="padded-right"
              >
                <input
                  v-model="interactionEvent"
                  :id="swapEvent"
                  :value="swapEvent"
                  type="radio"
                >
                <label :for="swapEvent">
                  {{ swapEvent }}
                </label>
              </span>
            </span>
          </div>

          <div class="dashboard__row">
            <span class="dashboard__row-label">Swapped:</span>
            <span class="dashboard__row-content">
              <span>
                <input
                  v-model="status"
                  id="swapStatus"
                  type="checkbox"
                >
                <label for="swapStatus">
                  force
                </label>
              </span>
            </span>
          </div>
        </div>
      </div>

      <div class="dashboard--right">
        <div class="dashboard">
          <div class="dashboard__row">
            <span class="dashboard__row-label">Preview:</span>
            <vue-swappable-card
              :direction="direction"
              :event="interactionEvent"
              :swapped="status"
            >
              <template #content-primary>
                <h1>Front Face</h1>
                <div class="card-body">
                  <img src="https://picsum.photos/seed/abc1/100">
                  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec nec malesuada ipsum. Morbi sit amet sagittis justo. Praesent non est eu lorem rhoncus scelerisque eget non nisi.</p>
                </div>
              </template>
              <template #content-secondary>
                <h1>Back Face</h1>
                <div class="card-body">
                  <img src="https://picsum.photos/seed/cba/100">
                  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec nec malesuada ipsum. Morbi sit amet sagittis justo. Praesent non est eu lorem rhoncus scelerisque eget non nisi.</p>
                </div>
              </template>
            </vue-swappable-card>
          </div>
        </div>
      </div>
    </div>

    <div class="bottom-links">
      <a
        href="https://github.com/dafcoe/vue-swappable-card"
        target="_blank"
      >
        <span
          v-html="icons.github"
          class="bottom-link--github"
        />
      </a>
      <a
        href="https://www.npmjs.com/package/@dafcoe/vue-swappable-card"
        target="_blank"
      >
        <span
          v-html="icons.npm"
          class="bottom-link--npm"
        />
      </a>
    </div>
  </div>
</template>

<script lang="ts">
import {
  defineComponent,
  reactive,
  toRefs,
} from 'vue'
import VueSwappableCard from '@/components/VueSwappableCard.vue'

export default defineComponent({
  name: 'App',
  components: {
    VueSwappableCard,
  },
  setup() {
    const swap = reactive({
      direction: 'from-bottom',
      interactionEvent: 'over',
      status: false,
    })

    const icons = {
      github: `
        <svg width="24px" height="24px" viewBox="0 0 24 24" role="img" xmlns="http://www.w3.org/2000/svg" fill="currentColor">
            <path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/>
        </svg>
      `,
      npm: `
        <svg width="24px" height="24px" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" fill="currentColor">
          <g>
              <rect width="24" height="24" opacity="0"/>
              <path d="M18 3H6a3 3 0 0 0-3 3v12a3 3 0 0 0 3 3h7V11h4v10h1a3 3 0 0 0 3-3V6a3 3 0 0 0-3-3z"/>
          </g>
        </svg>
      `,
    }

    return {
      ...toRefs(swap),
      icons,
    }
  },
})
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;500&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Source+Code+Pro&display=swap');

  body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    width: 100%;
    font-family: 'Roboto', sans-serif;
    font-weight: 300;
    line-height: 1.5;
    color: #333;
    background: url("https://www.transparenttextures.com/patterns/wall-4-light.png"), linear-gradient(to right, #2c3e50, #4ca1af);
  }

  * {
    box-sizing: border-box;
  }

  .title {
    margin-top: -40px;
    text-align: center;
    color: white;
    font-weight: 300;
    font-size: 64px;
  }

  .wrapper {
    display: flex;
  }

  .dashboard {
    display: flex;
    flex-direction: column;
    padding: 20px;
    width: 100%;
    max-width: 545px;
    background-color: rgba(255, 255, 255, .1);
    border-radius: 10px;
    backdrop-filter: blur(5px);
    border: 1px solid rgba(255, 255, 255, .125);
    border-top-color: rgba(255, 255, 255, .25);
    border-left-color: rgba(255, 255, 255, .25);
    color: #eee;

    &:not(:last-of-type) {
      margin-bottom: 20px;
    }

    &--left,
    &--right {
      margin: 10px;
    }

    &--left {
      .dashboard {
        height: 100%;
      }
    }

    &__row {
      display: flex;
      align-items: center;

      &:not(:last-of-type) {
        margin-bottom: 20px;
        padding-bottom: 20px;
        border-bottom: 1px solid rgba(255, 255, 255, .07);
      }
    }

    &__row-label {
      margin-right: 20px;
      font-weight: bold;
    }

    &__row-content {
      display: flex;
      justify-content: space-between;
      flex: 1;
    }

    .padded-right {
      margin-right: 50px;
    }

    input[type=radio],
    input[type=checkbox] {
      position: absolute;
      left: -100vw;

      &:checked {
        ~ label {
          border-color: rgba(255, 255, 255, .75);
        }
      }
    }

    label {
      padding: 8px;
      border: 1px solid transparent;
      border-radius: 5px;
      cursor: pointer;
      transition: all .25s ease-in;

      &:hover {
        border-color: rgba(255, 255, 255, .25);
      }
    }
  }

  .vsc {
    max-width: 380px;
    margin: 12px 12px 12px 0;

    .vsc__content {
      &--primary {
        h1 {
          background-color: darkcyan;
          color: white;
        }
      }

      &--secondary {
        h1 {
          color: #005858;
        }

        &::before {
          content: '';
          position: absolute;
          top: 0;
          bottom: 0;
          left: 0;
          z-index: -1;
          background-color: #20c69c;
          width: 88px;
        }
      }
    }

    h1 {
      margin: 0;
      padding: 12px;
    }

    img {
      float: right;
      border-radius: 4px;
      border: 1px solid #eee;
    }

    p {
      margin: 0;
      padding: 0;

      &:not(:last-of-type) {
        margin-bottom: 12px;
      }
    }

    .card-body {
      padding: 12px;
    }
  }

  .bottom-links {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    display: flex;
    justify-content: center;
    align-items: center;

    a {
      display: inline-block;
      margin: 0 10px;
      color: white;
      text-decoration: none;
      opacity: .75;
      transition: opacity .25s ease-in-out;

      &:hover {
        opacity: 1;
      }

      span {
        display: inline-flex;
        height: 42px;
        width: 42px;

        &.bottom-link--github {
          margin-top: -5px;
          padding: 5px;
        }
      }

      svg {
        height: 100%;
        width: 100%;
      }
    }

    :visited {
      color: white;
    }
  }
</style>
