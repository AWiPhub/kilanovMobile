<template>
  <Page class="page">
    <ActionBar title="Длина и расстояние" class="action-bar">
      <NavigationButton
        text="Назад"
        android.systemIcon="ic_menu_back"
        @tap="goBack"
      />
    </ActionBar>
    <ScrollView>
      <FlexboxLayout flexDirection="column">
        <FlexboxLayout
          flexDirection="row"
          alignItems="center"
          justifyContent="space-around"
          style="margin-top: 100px"
        >
          <FlexboxLayout flexDirection="row" alignItems="center">
            <Label class="labelPicker" text="Из" />
            <ListPicker
              class="listPicker"
              v-model="selectedOut"
              :items="listOfItems"
              selectedIndex="0"
            />
          </FlexboxLayout>
          <FlexboxLayout flexDirection="row" alignItems="center">
            <Label class="labelPicker" text="В" />
            <ListPicker
              class="listPicker"
              v-model="selectedTo"
              :items="listOfItems"
              selectedIndex="0"
            />
          </FlexboxLayout>
        </FlexboxLayout>

        <FlexboxLayout
          flexDirection="row"
          justifyContent="center"
          alignItems="center"
          style="margin-top: 50px; font-size: 22px"
        >
          <Label :text="total" />
        </FlexboxLayout>

        <FlexboxLayout
          flexDirection="row"
          justifyContent="center"
          style="margin-top: 100px"
        >
          <GridLayout columns="70, 70, 70" rows="65, 65, 65, 65, 65, 65, 65">
            <label
              :text="displayField"
              row="0"
              col="0"
              colSpan="3"
              class="display"
            />

            <button
              class="kp"
              text="C"
              row="1"
              col="0"
              colSpan="2"
              @tap="clear"
            />
            <button class="kp" text="⌫" row="1" col="2" @tap="backspace" />

            <button class="kp" text="7" row="2" col="0" @tap="input('7')" />
            <button class="kp" text="8" row="2" col="1" @tap="input('8')" />
            <button class="kp" text="9" row="2" col="2" @tap="input('9')" />

            <button class="kp" text="4" row="3" col="0" @tap="input('4')" />
            <button class="kp" text="5" row="3" col="1" @tap="input('5')" />
            <button class="kp" text="6" row="3" col="2" @tap="input('6')" />

            <button class="kp" text="1" row="4" col="0" @tap="input('1')" />
            <button class="kp" text="2" row="4" col="1" @tap="input('2')" />
            <button class="kp" text="3" row="4" col="2" @tap="input('3')" />

            <button
              class="kp"
              text="0"
              row="5"
              col="0"
              colSpan="3"
              @tap="input('0')"
            />

            <button
              class="kp"
              style="font-size: 16px"
              text="Конвертировать"
              row="6"
              col="0"
              colSpan="3"
              @tap="doConvertig"
            />
          </GridLayout>
        </FlexboxLayout>
      </FlexboxLayout>
    </ScrollView>
  </Page>
</template>

<script>
import Converter from "../Converter.vue";

export default {
  name: "Calc",
  data() {
    return {
      displayField: "",
      //             0      1     2    3     4
      listOfItems: ["мм", "см", "дм", "м", "км"],
      selectedOut: 0,
      selectedTo: 0,
      total: "",
    };
  },
  methods: {
    input(key) {
      if (["1", "2", "3", "4", "5", "6", "7", "8", "9", "0"].includes(key)) {
        this.displayField += key;
      }
    },
    backspace() {
      this.displayField = this.displayField.substr(
        0,
        this.displayField.length - 1
      );
    },
    clear() {
      this.displayField = "";
    },
    goBack() {
      this.$navigateTo(Converter);
    },
    doConvertig() {
      if (this.selectedOut == 0) {
        if (this.selectedTo == 0) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${this.displayField} ${this.listOfItems[this.selectedTo]}`;
        }
        if (this.selectedTo == 1) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 0.1} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 2) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 0.01} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 3) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 0.001} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 4) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 0.000001} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
      }

      if (this.selectedOut == 1) {
        if (this.selectedTo == 0) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 10} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 1) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField)} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 2) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 0.1} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 3) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 0.01} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 4) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 0.00001} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
      }

      if (this.selectedOut == 2) {
        if (this.selectedTo == 0) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 100} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 1) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 10} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 2) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 1} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 3) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 0.1} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 4) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 0.0001} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
      }

      if (this.selectedOut == 3) {
        if (this.selectedTo == 0) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 1000} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 1) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 100} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 2) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 10} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 3) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 1} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 4) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 0.001} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
      }

      if (this.selectedOut == 4) {
        if (this.selectedTo == 0) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 1000000} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 1) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 100000} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 2) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 10000} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 3) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 1000} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
        if (this.selectedTo == 4) {
          this.total = `${this.displayField} ${
            this.listOfItems[this.selectedOut]
          } = ${Number(this.displayField) * 1} ${
            this.listOfItems[this.selectedTo]
          }`;
        }
      }
    },
  },
  computed: {
    viewSelectedOut: function () {
      return this.listOfItems[this.selectedOut];
    },
  },
};
</script>

<style>
.listPicker {
  height: 350px;
  margin-left: 50px;
}
.labelPicker {
  font-size: 24px;
}
</style>
