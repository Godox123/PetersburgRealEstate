<template>
  <div class="navigation">
    <input
      placeholder="Введите ЖК / корпус / № квартиры / № паркинга"
      class="navigation__filter navigation__filter--search"
    />

    <div
      ref="types"
      :class="{ 'navigation__filter--active': isTypesVisible }"
      class="navigation__filter navigation__filter--types"
    >
      <div @click="toggle()" class="navigation__type-selected">
        {{ selectedStatus }}
      </div>

      <div class="navigation__items">
        <div v-for="item in types" :key="item.id" class="navigation__item">
          <input
            :id="item.id"
            style="display: none"
            type="checkbox"
            v-model="item.active"
          />

          <label
            :for="item.id"
            :class="{ 'navigation__label--active': item.active }"
            class="navigation__label"
          >
            <div
              :class="{ 'navigation__checkbox--active': item.active }"
              class="navigation__checkbox"
            ></div>

            <div class="navigation__text">{{ item.name }}</div>
          </label>
        </div>
      </div>
    </div>

    <div class="navigation__filter navigation__filter--basket">
      Очистить корзину
    </div>
  </div>
</template>

<script>
export default {
  name: "Navigation",

  created() {
    // Здесь может запускать какая то функция для выполнения поиска
    this.$watch(this.searchValue, (newVal) => {});
  },

  computed: {
    selectedStatus() {
      let res = "";

      this.types.forEach((t) => {
        if (t.active) {
          res = res + t.name + ",";
        }
      });

      return res ? res.slice(0, res.length - 1) : "Все статусы";
    },
  },

  data() {
    return {
      searchValue: "",
      isTypesVisible: false,
      types: [
        { id: 1, name: "Забронировано", active: false },
        { id: 2, name: "Продано", active: false },
        { id: 3, name: "Активно", active: false },
      ],
    };
  },

  mounted() {
    window.addEventListener("click", (e) => {
      if (!this.$refs["types"].contains(e.target)) {
        this.isTypesVisible = false;
      }
    });
  },

  methods: {
    toggle() {
      this.isTypesVisible = !this.isTypesVisible;
    },
  },
};
</script>

<style>
.navigation {
  display: grid;
  grid-template-columns: 637px 190px 154px;
  grid-column-gap: 10px;
  margin: 0 auto 32px auto;
}

.navigation__filter {
  font: 400 14px/32px "PTSans";
  background: rgba(0, 0, 0, 0) no-repeat;
}

.navigation__filter--search {
  border: 1px solid #c4c4c4;
  padding: 0 46px 0 46px;
  background-image: url(i/search.svg);
  background-size: 14px 14px;
  background-position: 13px 50%;
}

.navigation__filter--search::placeholder {
  color: #9b9b9b;
}

.navigation__filter--types {
  border: 1px solid #c4c4c4;
  padding: 0 30px 0 15px;
  cursor: pointer;
  position: relative;
}

.navigation__filter--types::after {
  content: "";
  width: 7px;
  height: 5px;
  position: absolute;
  right: 13px;
  top: 0;
  bottom: 0;
  margin: auto;
  background: url(i/tick.svg) no-repeat 50% 50% / cover;
  transition: transform 0.4s;
  transform: rotate(180deg);
}

.navigation__filter--active::after {
  transform: rotate(0deg);
}

.navigation__type-selected {
  width: 100%;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
}

.navigation__filter--basket {
  cursor: pointer;
  background: #e5e5e5 url(i/close.svg) no-repeat 90% 50% /12px 12px;
  padding: 0 40px 0 13px;
  font-size: 13px;
  line-height: 33px;
}
</style>

<style>
.navigation__items {
  z-index: 2;
  position: absolute;
  opacity: 0;
  visibility: hidden;
  transition: 0.4s;
  background: #ffffff;
  box-shadow: 0px 20px 25px -5px rgba(26, 32, 44, 0.1),
    0px 10px 10px -5px rgba(26, 32, 44, 0.04);
  padding: 17px 20px 2px 20px;
  transform: translate(0, -15px);
  width: 100%;
  left: 0;
}

.navigation__filter--active .navigation__items {
  opacity: 1;
  visibility: visible;
  transform: translate(0, 5px);
}

.navigation__label {
  display: flex;
  align-items: center;
  margin: 0 0 15px 0;
  cursor: pointer;
}

.navigation__checkbox {
  width: 16px;
  height: 16px;
  border: 1px solid #c4c4c4;
  margin: 0 15px 0 0;
}

.navigation__label--active .navigation__checkbox {
  background-color: #fce66f;
  background-image: url(i/galka.svg);
  background-position: 50%;
  background-repeat: no-repeat;
}

.navigation__text {
  font: 400 14px/18px "PTSans";
  transition: color 0.2s;
}

.navigation__text:hover {
  color: #ff0d29;
}
</style>
