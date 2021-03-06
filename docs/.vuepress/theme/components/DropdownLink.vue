<template>
  <div class="dropdown-wrapper" :class="{ open }">
    <a class="dropdown-title" @click="toggle">
      <span class="title">{{ item.text }}</span>
      <!-- @TODO 向下箭头 -->
      <!-- <span class="arrow" :class="open ? 'down' : 'right'"></span> -->
    </a>

    <DropdownTransition>
        <ul class="nav-dropdown animated fadeIn" v-show="open">
          <li
            class="dropdown-item"
            :key="subItem.link || index"
            v-for="(subItem, index) in item.items"
          >
            <h4 v-if="subItem.type === 'links'">{{ subItem.text }}</h4>

            <ul class="dropdown-subitem-wrapper" v-if="subItem.type === 'links'">
              <li
                class="dropdown-subitem"
                :key="childSubItem.link"
                v-for="childSubItem in subItem.items"
              >
                <NavLink :item="childSubItem"/>
              </li>
            </ul>

            <NavLink v-else :item="subItem"/>
          </li>
        </ul>
    </DropdownTransition>
  </div>
</template>

<script>
import NavLink from "./NavLink.vue";
import DropdownTransition from "./DropdownTransition.vue";

export default {
  components: { NavLink, DropdownTransition },

  data() {
    return {
      open: false
    };
  },

  props: {
    item: {
      required: true
    }
  },

  methods: {
    toggle() {
      this.open = !this.open;
    }
  }
};
</script>

<style lang="stylus">
@import './../styles/config.styl';

.dropdown-wrapper {
  cursor: pointer;

  .dropdown-title {
    display: block;

    &:hover {
      border-color: transparent;
    }

    .arrow {
      vertical-align: middle;
      margin-top: -1px;
      margin-left: 0.4rem;
    }
  }

  .nav-dropdown {
    .dropdown-item {
      line-height: 40px;
      font-size: 10px;
      padding: 10px 20px;
      // border-bottom: 1px dashed #e7e7e9;
      color: #565656;
      line-height: 1.7rem;

      &:last-child {
        // border: 0 dashed #e7e7e9;
      }

      h4 {
        margin: 0.45rem 0 0;
        border-top: 1px solid #eee;
        padding: 0.45rem 1.5rem 0 1.25rem;
      }

      .dropdown-subitem-wrapper {
        padding: 0;
        list-style: none;

        .dropdown-subitem {
          font-size: 0.9em;
        }
      }

      a {
        display: block;
        line-height: 1.7rem;
        position: relative;
        border-bottom: none;
        font-weight: 400;
        margin-bottom: 0;
        padding: 0 1.5rem 0 1.25rem;

        &:hover {
          color: $accentColor;
        }

        &.router-link-active {
          color: $accentColor;

          &::after {
            content: '';
            width: 0;
            height: 0;
            border-left: 5px solid $accentColor;
            border-top: 3px solid transparent;
            border-bottom: 3px solid transparent;
            position: absolute;
            top: calc(50% - 2px);
            left: 9px;
          }
        }
      }

      &:first-child h4 {
        margin-top: 0;
        padding-top: 0;
        border-top: 0;
      }
    }
  }
}

@media (max-width: $MQMobile) {
  .dropdown-wrapper {
    &.open .dropdown-title {
      margin-bottom: 0.5rem;
    }

    .nav-dropdown {
      transition: height 0.1s ease-out;
      overflow: hidden;

      .dropdown-item {
        padding: 0;
        border-bottom: 0px dashed #e7e7e9;

        h4 {
          border-top: 0;
          margin-top: 0;
          padding-top: 0;
        }

        h4, & > a {
          font-size: 12px;
          line-height: 2rem;
          border-left: 1px dashed #e7e7e9;
        }

        .dropdown-subitem {
          font-size: 12px;
          padding-left: 1rem;
        }
      }
    }
  }
}

@media (min-width: $MQMobile) {
  .dropdown-wrapper {
    height: 1.8rem;

    &:hover .nav-dropdown {
      // override the inline style.
      display: block !important;
    }

    .dropdown-title .arrow {
      // make the arrow always down at desktop
      border-left: 4px solid transparent;
      border-right: 4px solid transparent;
      border-top: 6px solid $arrowBgColor;
      border-bottom: 0;
    }

    .nav-dropdown {
      // Avoid height shaked by clicking
      // height: auto !important;
      box-shadow: 0 0.067em 1.2em rgba(0,0,0,.14);
      box-sizing: border-box;
      max-height: calc(100vh - 2.7rem);
      overflow-y: auto;
      position: absolute;
      top: 100%;
      right: 50%;
      transform: translateX(50%);
      background-color: #fff;
      padding: 0.6rem 0;
      border: 1px solid #ddd;
      border-bottom-color: #ccc;
      text-align: left;
      border-radius: 0.25rem;
      white-space: nowrap;
      margin: 0;
    }
  }
}
</style>
