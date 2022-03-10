<template>
  <div class="items">
    <Item v-for="i in flats" :key="i.id" :i="i"></Item>
    <Item v-for="i in parking" :key="i.id" :i="i"></Item>
  </div>
</template>

<script>
import Item from "../item/item.vue";

import plan from "./i/plan.png";

export default {
  name: "Items",
  components: {
    Item,
  },

  computed: {
    flats() {
      return this.items.filter((i) => i.type.slug === "flat");
    },
    parking() {
      return this.items.filter((i) => i.type.slug === "parking");
    },
  },

  data() {
    return {
      items: [
        {
          id: 12,
          isActive: false,
          price: "7 733 300 руб.",
          type: { slug: "flat", name: "Квартира" },
          status: { slug: "entity", text: "Уступка от юр. лица" },
          address: {
            name: "Чистое Небо",
            value: ", корпус 10, III кв. 2022 г.",
          },
          apnumber: "кв. 62",
          rooms: "1 комн. кв.",
          location:
            "Лен. область, Всеволожский район,д. Кудрово, ул. Столичная, д. 5, к. 1",
          plan,
          squares: "234.38 м²",
          floor: "7 этаж",
          date: "21/11/2020",
        },
        {
          id: 13,
          isActive: false,
          price: "7 733 300 руб.",
          type: { slug: "flat", name: "Квартира" },
          status: { slug: "person", text: "Уступка от физ. лица" },
          address: {
            name: "Зеленый квартал на Пулковских высотах,",
            value: " корпус 10, III кв. 2022 г.",
          },
          apnumber: "кв. 62",
          rooms: "1 комн. кв.",
          location: "Комендантский пр., уч. 1 Каменка",
          plan,
          squares: "234.38 м²",
          floor: "7 этаж",
          date: "21/11/2020",
        },

        {
          id: 22,
          isActive: false,
          price: "800 300 руб.",
          type: { slug: "parking", name: "Паркинг" },
          status: { slug: "booked", text: "Забронировано" },
          address: {
            name: "Зеленый квартал на Пулковских высотах,",
            value: " корпус 10, III кв. 2022 г.",
          },
          number: "№ 7-10-2 (ПИБ №68)",
          size: "15 м²",
          location:
            "Ленинградская область, Всеволожский район, д. Кудрово, ул. Столичная, д. 5, к. 1",
          plan,
          date: "21/11/2020",
        },

        {
          id: 23,
          isActive: false,
          price: "800 300 руб.",
          type: { slug: "parking", name: "Паркинг" },
          status: { slug: "sold", text: "Продано" },
          address: {
            name: "Зеленый квартал на Пулковских высотах,",
            value: " корпус 10, III кв. 2022 г.",
          },
          number: "№ 7-10-2 (ПИБ №68)",
          size: "15 м²",
          location:
            "Лен. область, Всеволожский район, д. Кудрово, ул. Столичная, д. 5, к. 1",
          plan,
          date: "21/11/2020",
        },
      ],
    };
  },
};
</script>

<style>
.items {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}
</style>
