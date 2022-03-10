<template>
  <div class="func">
    <input id="all" type="checkbox" v-model="all" style="display: none" />
    <label for="all" class="func__label">
      <div
        :class="{ 'func__checkbox--active': all }"
        class="func__checkbox"
      ></div>
      <div class="func__text">все</div>
    </label>
    <div class="func__button func__button--save">Сохранить</div>
    <div class="func__button func__button--send">Отправить</div>
    <div class="func__button func__button--remove">Удалить</div>
  </div>
</template>

<script>
export default {
  name: "Func",

  data() {
    return {
      all: false,
    };
  },
};
</script>

<style>
.func {
  padding: 0 0 0 25px;
  display: flex;
  margin: 0 0 20px 0;
}
.func__label {
  margin: 0 13px 0 0;
  display: flex;
  align-items: center;
  cursor: pointer;
  height: 38px;
}

.func__checkbox {
  width: 16px;
  height: 16px;
  border: 1px solid #c4c4c4;
  margin: 0 10px 0 0;
}

.func__checkbox--active {
  background-color: #fce66f;
  background-image: url(i/galkaFunc.svg);
  background-position: 50%;
  background-repeat: no-repeat;
}

.func__text {
  font: 400 13px/20px "PTSans";
}

.func__button {
  background: #e5e5e5 no-repeat;
  height: 38px;
  margin: 0 10px 0 0;
  padding: 0 43px 0 13px;
  font: 400 13px/38px "PTSans";
  cursor: pointer;
}

.func__button--save {
  background-image: url(i/pdf.svg);
  background-size: 13px 15px;
  background-position: 84px 50%;
}

.func__button--send {
  background-image: url(i/send.svg);
  background-size: 14px 14px;
  background-position: 84px 50%;
}

.func__button--remove {
  background-image: url(i/remove.svg);
  background-size: 13px 15px;
  background-position: 68px 45%;
}
</style>
