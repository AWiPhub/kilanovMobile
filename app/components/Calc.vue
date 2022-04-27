<template>
  <Page class="page">
    <ActionBar title="Калькулятор" class="action-bar">
      <NavigationButton
        text="Назад"
        android.systemIcon="ic_menu_back"
        @tap="goBack"
      />
    </ActionBar>
    <ScrollView>
      <FlexboxLayout class="layout">
        <GridLayout
          columns="70, 70, 70, 70"
          rows="65, 65, 65, 65, 65, 65"
          class="background"
        >
          <label
            :text="displayField"
            row="0"
            col="0"
            colSpan="4"
            class="display"
          />

          <button class="kp" text="C" row="1" col="0" @tap="clear" />
          <button class="kp" text="^" row="1" col="1" @tap="input('^')" />
          <button class="kp" text="/" row="1" col="2" @tap="input('/')" />
          <button class="kp" text="*" row="1" col="3" @tap="input('*')" />

          <button class="kp" text="7" row="2" col="0" @tap="input('7')" />
          <button class="kp" text="8" row="2" col="1" @tap="input('8')" />
          <button class="kp" text="9" row="2" col="2" @tap="input('9')" />
          <button class="kp" text="-" row="2" col="3" @tap="input('-')" />

          <button class="kp" text="4" row="3" col="0" @tap="input('4')" />
          <button class="kp" text="5" row="3" col="1" @tap="input('5')" />
          <button class="kp" text="6" row="3" col="2" @tap="input('6')" />
          <button class="kp" text="+" row="3" col="3" @tap="input('+')" />

          <button class="kp" text="1" row="4" col="0" @tap="input('1')" />
          <button class="kp" text="2" row="4" col="1" @tap="input('2')" />
          <button class="kp" text="3" row="4" col="2" @tap="input('3')" />
          <button
            class="kp"
            text="="
            row="4"
            col="3"
            rowSpan="2"
            @tap="doCalc"
          />

          <button
            class="kp"
            text="0"
            row="5"
            col="0"
            colSpan="2"
            @tap="input('0')"
          />
          <button class="kp" text="." row="6" col="2" @tap="input('.')" />
        </GridLayout>
      </FlexboxLayout>
    </ScrollView>
  </Page>
</template>

<script>
import Home from "./Home.vue";

export default {
  name: "Calc",
  methods: {
    clear() {
      this.displayField = "";
    },

    input(key) {
      if (["1", "2", "3", "4", "5", "6", "7", "8", "9", "0"].includes(key)) {
        this.displayField += key;
      }

      if (["+", "-", "*", "/", "^"].includes(key)) {
        if (
          !["+", "-", "*", "/", "^", "."].includes(
            this.displayField.slice(-1)
          ) &&
          this.displayField !== ""
        ) {
          this.displayField += key;
        } else if (this.displayField === "") {
          return;
        } else {
          this.displayField =
            this.displayField.substring(0, this.displayField.length - 1) + key;
        }
      }

      if (["."].includes(key)) {
        if (
          !["+", "-", "*", "/", "^", "."].includes(
            this.displayField.slice(-1)
          ) &&
          this.displayField !== ""
        ) {
          this.displayField += key;
        } else {
          return;
        }
      }
    },

    doCalc() {
      if (this.displayField.indexOf("^") !== -1) {
        this.displayField
          .match(/\d+(\.\d+)?\^(\-|\+)?\d+(\.\d+)?/gi)
          .map((row) => {
            const nums = row.split("^");
            this.displayField = this.displayField.replace(
              row,
              `Math.pow(${nums[0]},${nums[1]})`
            );
          });
        if (eval(this.displayField) == Infinity) {
          if (this.displayField.match(/\d+(\.\d+)?\/0/gi)) {
            alert({
              title: "Ошибка!",
              message: "Делить на 0 нельзя",
              okButtonText: "Больше так не буду",
            });
          } else {
            this.displayField = "";
            alert({
              title: "!!! ОШИБКА !!!",
              message:
                "Вы сделали что-то не так, либо получившееся число СЛИШКОМ большое",
              okButtonText: "Ну ладно",
            });
          }
        } else {
          this.displayField = eval(this.displayField).toString();
        }
      } else {
        if (eval(this.displayField) == Infinity) {
          if (this.displayField.match(/\d+(\.\d+)?\/0/gi)) {
            alert({
              title: "Ошибка",
              message: "Делить на 0 нельзя",
              okButtonText: "Ок",
            });
          } else {
            this.displayField = "";
            alert({
              title: "Ошибка",
              message: "Что-то не так",
              okButtonText: "Ну ладно",
            });
          }
        } else {
          this.displayField = eval(this.displayField).toString();
        }
      }
    },

    goBack() {
      this.$navigateTo(Home);
    },
  },

  data() {
    return {
      displayField: "",
    };
  },
};
</script>

<style>
.layout {
  padding-top: 250px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.background {
  padding: 40px;
  border-radius: 60px;
}

.display {
  background: #000000;
  padding-top: 10px;
  padding-right: 40px;
  font-size: 28px;
  text-align: right;
  border-radius: 35px;
  max-height: 160px;
  height: 160px;
  overflow-wrap: normal;
}

.kp {
  margin: 20px;
  background-color: #2f4958;
  box-shadow: 0 15px 0 #1f2d36;
  font-size: 28px;
  border-radius: 35px;
  text-align: center;
  padding-top: 10px;
}
.kp:active {
  margin: 40px 20px 20px 20px;
  box-shadow: 0 5px 0 #1f2d36;
  background-color: #9bafbb;
}
</style>
