<template>
  <Page class="page">
    <ActionBar title="Конвертер" class="action-bar">
      <NavigationButton
        text="Назад"
        android.systemIcon="ic_menu_back"
        @tap="goBack"
      />
    </ActionBar>
    <ScrollView>
      <FlexboxLayout flexDirection="column" justifyContent="center">
        <FlexboxLayout
          flexDirection="column"
          justifyContent="center"
          alignItems="center"
          class="converterType"
          row="0"
          col="0"
          @tap="goTo('measure')"
        >
          <Label> Длина и расстояние </Label>
        </FlexboxLayout>
        <FlexboxLayout
          flexDirection="column"
          justifyContent="center"
          alignItems="center"
          class="converterType"
          row="0"
          col="1"
          @tap="goTo('temp')"
        >
          <Label> Температура </Label>
        </FlexboxLayout>
        <FlexboxLayout
          flexDirection="column"
          justifyContent="center"
          alignItems="center"
          class="converterType"
          row="1"
          col="0"
          @tap="goTo('binary')"
        >
          <Label textWrap> Единицы хранения цифровой информации </Label>
        </FlexboxLayout>
      </FlexboxLayout>
    </ScrollView>
  </Page>
</template>

<script>
import Home from "./Home.vue";

import Measure from "./converterTypes/measure.vue";
import Temp from "./converterTypes/temp.vue";
import Binary from "./converterTypes/binary.vue";

export default {
  name: "Converter",
  methods: {
    goTo(place) {
      switch (place) {
        case "measure":
          this.$navigateTo(Measure);
          break;
        case "temp":
          this.$navigateTo(Temp);
          break;
        case "binary":
          this.$navigateTo(Binary);
          break;
      }
    },
    goBack() {
      this.$navigateTo(Home);
    },
  },

  data() {
    return {};
  },
};
</script>

<style>
.converterType {
  margin: 50px;
  height: 200px;
  background-color: #3c3c3c;
  text-align: center;
  font-size: 12px;
}
.iconConverter {
  width: 190px;
  height: 190px;
  margin-bottom: 30px;
}
</style>
