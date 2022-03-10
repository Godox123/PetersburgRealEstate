<template>
  <div class="item">
    <input
      type="checkbox"
      v-model="i.isActive"
      style="display: none"
      :id="i.id"
    />

    <label :for="i.id" class="item__label">
      <div
        :class="{ 'item__checkbox--active': i.isActive }"
        class="item__checkbox"
      ></div>
    </label>
    <div class="item__center">
      <div class="item__wrap item__wrap--price">
        <div class="item__price">{{ i.price }}</div>
        <div
          :class="{ 'item__type--parking': i.type.slug === 'parking' }"
          class="item__type"
        >
          <span ref="type">{{ i.type.name }}</span>
        </div>
      </div>
      <div class="item__address">
        <span class="item__address-name">{{ i.address.name }}</span>
        <span class="item__address-val"> {{ i.address.value }}</span>
      </div>
      <div v-if="i.type.slug === 'flat'" class="item__tabs">
        <div class="item__tab item__tab--left">
          <div class="item__text">{{ i.apnumber }}</div>
          <div class="item__text">{{ i.rooms }}</div>
        </div>
        <div class="item__tab item__tab--right">
          <div class="item__text">{{ i.squares }}</div>
          <div class="item__text">{{ i.floor }}</div>
        </div>
      </div>

      <div v-if="i.type.slug === 'parking'" class="item__tabs">
        <div class="item__tab item__tab--left">
          <div class="item__text">{{ i.number }}</div>
        </div>
        <div class="item__tab item__tab--right">
          <div class="item__text">{{ i.size }}</div>
        </div>
      </div>

      <div class="item__location">{{ i.location }}</div>
    </div>
    <div class="item__right">
      <div :class="`item__status--${i.status.slug}`" class="item__status">
        {{ i.status.text }}
      </div>
      <div class="item__img-wrap">
        <img :src="i.plan" alt="" class="item__img" />
      </div>
      <div class="item__date">Добавлено {{ i.date }}</div>
    </div>
  </div>
</template>

<script>
import tippy from "tippy.js";
import "tippy.js/animations/scale.css";
import "tippy.js/dist/tippy.css";

export default {
  name: "Item",
  props: ["i"],

  mounted() {
    tippy(this.$refs["type"], {
      content: "Подземная встроенно-пристроенная",
      animation: "scale",
      theme: "black",
      arrow: true,
      placement: "bottom-start",
    });
  },
};
</script>

<style>
.tippy-box[data-theme~="black"] {
  background-color: rgba(0, 0, 0, 0.6);
  color: #fff;
  padding: 0 18px;
  font: 400 13px/20px "PTSans";
  height: 44px;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0px 8px 30px -3px rgba(26, 32, 44, 0.1),
    0px 4px 6px -2px rgba(26, 32, 44, 0.05);
}
.tippy-box[data-theme~="black"] > .tippy-arrow:before {
  border-bottom-color: rgba(0, 0, 0, 0.6) !important;
  border-top-color: rgba(0, 0, 0, 0.6) !important;
  top: -8px !important;
}
</style>

<style>
.item {
  background: #ffffff;
  border: 1px solid #e5e5e5;
  width: calc(50% - 11px);
  margin: 0 0 23px 0;
  height: 238px;
  padding: 25px 0 25px 66px;
  display: flex;
  justify-content: space-between;
  position: relative;
}

.item__wrap {
  display: flex;
}

.item__wrap--price {
  margin: 0 0 3px 0;
}

.item__label {
  display: block;
  position: absolute;
  height: 100%;
  top: 0;
  left: 25px;
}

.item__checkbox {
  width: 16px;
  height: 16px;
  border: 1px solid #c4c4c4;
  position: absolute;
  margin: auto;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  cursor: pointer;
}

.item__checkbox--active {
  background-color: #fce66f;
  background-image: url(i/galkaitem.svg);
  background-position: 50%;
  background-repeat: no-repeat;
}
</style>

<style>
.item__price {
  color: #ff0d29;
  font: 700 15px/20px "PTSans";
  margin: 0 16px 0 0;
}

.item__type {
  cursor: pointer;
  height: 26px;
  font: 400 12px/26px "PTSans";
  padding: 0 16px 0 38px;
  background: #ffffff url(i/appicon.svg) no-repeat 15px 50%/14px 14px;
  box-shadow: 0px 0px 2px rgba(94, 119, 157, 0.25);
  border-radius: 32px;
  transform: translate(0px, -3px);
}

.item__type--parking {
  background-image: url(i/car.svg);
  background-size: 15px 14px;
}
</style>

<style>
.item__address {
  font: 400 14px/21px "PTSans";
  height: 42px;
  white-space: pre-line;
  margin: 0 0 10px 0;
  min-width: 230px;
}
.item__address-name {
  color: #000;
}

.item__address-val {
  color: rgb(191, 191, 191);
}
</style>

<style>
.item__tabs {
  display: flex;
  margin: 0 0 16px 0;
}

.item__tab--left {
  border-right: 1px solid #c4c4c4;
  padding: 0 20px 0 0;
}
.item__tab--right {
  padding: 0 0 0 20px;
}

.item__text {
  font: 400 14px/25px "PTSans";
}
</style>

<style>
.item__location {
  padding: 0 0 0 18px;
  transform: translate(-18px, 0px);
  position: absolute;
  bottom: 19px;
  font: 400 14px/21px "PTSans";
  max-width: 250px;
  white-space: pre-line;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -moz-box;
  -moz-box-orient: vertical;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  line-clamp: 2;
  box-orient: vertical;
  display: inline-block;
  vertical-align: text-bottom;
}

.item__location:before {
  content: "";
  position: absolute;
  width: 9px;
  height: 13px;
  display: block;
  background: url(i/marker.svg) 50% 50% no-repeat;
  left: 0px;
  top: 3px;
}
</style>

<style>
.item__right {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}

.item__status {
  font: 400 14px/30px "PTSans";
  padding: 0 9px 0 23px;
  position: relative;
  transform: translate(0, -4px);
  margin: 0 0 27px 0;
  white-space: nowrap;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  width: fit-content;
  width: -moz-fit-content;
}

.item__status:before {
  content: "";
  display: block;
  width: 6px;
  height: 6px;
  border-radius: 50%;
  position: absolute;
  left: 9px;
  top: 0;
  bottom: 0;
  margin: auto;
}

.item__status--entity {
  background-color: #ffe4e4;
  color: #dd4c5d;
}

.item__status--entity:before {
  background-color: #dd4c5d;
}

.item__status--person {
  background-color: #d6f5ff;
  color: #0291c1;
}

.item__status--person:before {
  background-color: #0291c1;
}

.item__status--booked {
  background-color: #ededed;
  color: #686868;
}

.item__status--booked:before {
  background-color: #686868;
}

.item__status--sold {
  background-color: #cccccc;
  color: #808080;
}

.item__status--sold:before {
  background-color: #808080;
}
</style>

<style>
.item__img-wrap {
  width: 127px;
  height: 0;
  padding: 0 0 98px 0;
  position: relative;
  margin: 0 25px 17px 0;
}
.item__img {
  position: absolute;
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>

<style>
.item__date {
  color: #9b9b9b;
  font: 400 13px/20px "PTSans";
  padding: 0 26px 0 0;
  white-space: nowrap;
}
</style>
