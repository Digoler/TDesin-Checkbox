<template>
  <h1>123</h1>
  <div class="person-list">
    <t-checkbox-group v-model:value="personOptions" class="horizontal-box">
      <div
        v-for="person in personList"
        :key="person.id"
        :class="`card ${
          personOptions.indexOf(person.name) > -1
            ? 'card--active'
            : personOptions.indexOf(person.name)
        }`"
      >
        <t-icon
          v-if="personOptions.indexOf(person.name) > -1"
          name="check"
          class="card__icon"
          :aria-hidden="true"
        />
        <t-checkbox
          :value="person.name"
          :label="person.name"
          icon="none"
          borderless
        />
      </div>
    </t-checkbox-group>
  </div>
  <div>This is personOptions：{{ personOptions }}</div>
  <button
    @click="changePersonOptions"
    style="
       {
        width: 100px;
        height: 50px;
      }
    "
  >
    点击往personOptions添加数据"蔡晓萱"
  </button>
  <div>问题：点击第二个多选框，personOptions中数据没变化</div>
</template>

<script setup lang="ts">
import { reactive, ref, watch } from "vue";
const personOptions = reactive(["蔡宣轩"]);
const personList = reactive([
  { id: 1, name: "蔡宣轩" },
  { id: 2, name: "蔡晓萱" },
]);
function changePersonOptions() {
  personOptions.push("蔡晓萱");
}
watch(personOptions, (value) => {
  console.log(value);
});
const value = ref([1, 2]);
</script>

<style scoped lang="less">
.font-style() {
  color: #000000e6;
  font-family: "PingFang SC";
  text-align: left;
}

.other-info-title {
  width: 249px;
  height: 24px;
  opacity: 1;
  color: #000000e6;
  font-size: 16px;
  font-weight: 600;
  font-family: "PingFang SC";
  text-align: left;
  line-height: 24px;
}

.order-info {
  display: inline-block;
  margin: 16px 16px 0 16px;
  width: 343px;
  font-size: 20px;
  font-weight: 600;
  line-height: 28px;
  .font-style();
  .activity-time-place {
    display: flex;
    align-items: center;
    margin-top: 8px;
    width: 278px;
    height: 22px;
    opacity: 1;
    color: #000000e6;
    font-size: 14px;
    font-weight: 400;
    font-family: "PingFang SC";
    text-align: left;
    line-height: 22px;
    .activity-time {
      margin-right: 16px;
    }
    .time-place-Icon {
      margin-right: 4px;
      display: inline-block;
      color: #0052d9;
    }
  }
  .other-info {
    width: 100%;
    height: 532px;
    .person-info {
      width: 100%;
      height: 96px;
      .person-info-title {
        display: flex;
        align-items: center;
        margin-top: 16px;
        width: 100%;
        height: 28px;
      }
      .person-list {
        margin-top: 14px;
        width: 100%;
        height: 56px;
      }
    }
    .ticket-info {
      width: 100%;
      height: 92px;
      margin-top: 24px;
    }
    .ticket-price-list {
      margin-top: 24px;
    }
  }
}

//纵向多选框
.card-column {
  margin-top: 12px;
  position: relative;
  width: 100%;
  height: 58px;
  border-radius: 6px;
  border: 1px solid #dcdcdc;
  background: #ffffff;
  margin-right: 16px;
  overflow: hidden;
}

//横线多个卡片样式
.card {
  position: relative;
  width: 107px;
  height: 58px;
  border-radius: 6px;
  border: 1px solid #dcdcdc;
  background: #ffffff;
  margin-right: 16px;
  overflow: hidden;
}
.card--active {
  border-color: #0052d9;
}
.card--active::after {
  content: "";
  display: block;
  position: absolute;
  left: 0;
  top: 0;
  width: 0;
  border: 14px solid #0052d9;
  border-bottom-color: transparent;
  border-right-color: transparent;
}
.card__icon {
  font-size: 12px;
  color: #fff;
  position: absolute;
  left: 1.5px;
  top: 1.5px;
  z-index: 1;
}
.t-checkbox {
  border-radius: 6px;
}
/* 横向布局 */
.horizontal-box {
  display: flex;
  justify-content: flex-start;
  align-items: center;
}

.horizontal-box .card__icon {
  font-size: 12px;
}

.purchase-confirm {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 375px;
  height: 80px;
  opacity: 1;
  border-top: 1px solid #e7e7e7;
  background: #fff;
  .price-text {
    display: flex;
    align-items: center;
    width: 102px;
    height: 28px;
    color: #000000e6;
    font-size: 14px;
    font-weight: 400;
    font-family: "PingFang SC";
    text-align: center;
    .price {
      width: 36px;
      height: 28px;
      color: #0052d9;
      font-size: 20px;
      font-weight: 600;
      text-align: center;
      line-height: 28px;
    }
  }
  .btn {
    width: 210px;
    height: 58px;
  }
}
</style>
