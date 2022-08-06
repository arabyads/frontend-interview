<script>
import ArrowDown from "../icons/ArrowDown.vue";

export default {
  components: {
    ArrowDown,
  },
  props: {},
  data() {
    return {
      options: [
        {
          id: 1,
          value: "Chahe",
        },
        {
          id: 2,
          value: "Pita",
        },
        {
          id: 3,
          value: "Pocito",
        },
        {
          id: 4,
          value: "Jiancha",
        },
        {
          id: 5,
          value: "Krasnoznamensk",
        },
        {
          id: 6,
          value: "Leceia",
        },
        {
          id: 7,
          value: "Yokosuka",
        },
        {
          id: 8,
          value: "Pobé",
        },
        {
          id: 9,
          value: "Baizhifang",
        },
        {
          id: 10,
          value: "Sawangan",
        },
        {
          id: 11,
          value: "Lamphun",
        },
        {
          id: 12,
          value: "Yanwo",
        },
        {
          id: 13,
          value: "Smętowo Graniczne",
        },
        {
          id: 14,
          value: "MacArthur",
        },
        {
          id: 15,
          value: "Ya‘bad",
        },
        {
          id: 16,
          value: "Lubochnia",
        },
        {
          id: 17,
          value: "Ventsy",
        },
        {
          id: 18,
          value: "Houston",
        },
        {
          id: 19,
          value: "Cartagena",
        },
        {
          id: 20,
          value: "Abbotsford",
        },
      ],
      value: [],
      isClearable: false,
      isMultiple: true,
      isSearchable: true,
      showMenu: false,
      searchText: "",
    };
  },

  computed: {},

  watch: {},

  methods: {
    toggleMenu() {
      this.showMenu = !this.showMenu;
    },

    closeMenu() {
      this.showMenu = false;
    },

    updateSelected() {},

    restInputValue() {},

    selectAll() {},

    search() {},
  },
};
</script>

<template>
  <div class="input-container">
    <label>Input label</label>
    <div
      class="
        d-flex
        justify-content-between
        align-items-center
        radius-8
        w-100
        m-y-6
        radius-8
        p-x-12 p-base-medium
        menu-activator
        role-input
      "
    >
      <div
        class="
          d-flex
          align-items-center
          m-r-9
          string-content-container
          nowrap-white-space
          value-container
          col
          p-0
        "
        @click="toggleMenu"
      ></div>
      <div class="d-flex align-items-center">
        <div>
          <span v-if="isClearable" @click="restInputValue">X</span>
        </div>
        <ArrowDown @click.native="toggleMenu" />
      </div>
    </div>
    <transition name="fadeUp">
      <ul v-if="showMenu" class="dropdown-menu">
        <div v-if="isSearchable" class="search-input-container">
          <input type="text" placeholder="search options"/>
        </div>
        <div class="dropdown-menu-content">
          <div v-if="!options.length" class="w-100 text-center">
            <span>There is no data to display</span>
          </div>
          <li v-if="isMultiple && options.length" class="" @click="selectAll">
            <span class="">(Un)Select All</span>
          </li>

          <template v-if="options.length">
            <li
              v-for="option in options"
              :key="option.index"
              class="
                option
                d-flex
                justify-content-between
                align-items-center
                flex-wrap
              "
              @click="updateSelected"
            >
              <div>
                <span class="">
                  {{ option.value }}
                </span>
              </div>
            </li>
          </template>
        </div>
      </ul>
    </transition>
  </div>
</template>

<style scoped lang='sass'>
.input-container
    position: relative
    top: 0
    bottom: 0
    right: 0
    left: 0
.menu-activator
    height: 30px
    border-radius: 4px
    padding: 4px
    min-width: 100px
    border: 1px solid
    max-width: 100%
    .value-container
        height: 100%
.dropdown-menu
    padding: 0
    width: 100%
    list-style: none
    z-index: 3
    position: absolute
    background: #fff
    box-shadow: 0px 15px 60px rgba(0, 0, 0, 0.12)
    overflow-y: scroll
    padding: 8px
    margin: 0
    .dropdown-menu-content
        max-height: 200px
        min-height: 50px
    .search-input-container
        width: 100%
        margin-bottom: 15px
        input
            width: 100%
    .option
        margin: 4px
    .option:hover
        background: #CD0B19
        color: #fff
        border-radius: 4px
        padding: 4px
        cursor: pointer
.unselected:hover
    background: rgba(6, 90, 116, 0.1)
    color: #CD0B19
.selected
    background: #CD0B19
.selected:hover
    color: #fff
</style>
