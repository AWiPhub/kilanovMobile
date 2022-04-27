<template>
  <Page class="page">
    <ActionBar title="Kilanov" class="action-bar" />
    <ScrollView>
      <FlexboxLayout flexDirection="column" justifyContent="center">
        <Button
          style="font-size: 14px"
          text="Калькулятор"
          @tap="goToDetailPage('calc')"
        />
        <Button
          style="font-size: 14px"
          text="Конвертер"
          @tap="goToDetailPage('converter')"
        />
        <Button
          style="font-size: 14px"
          text="Календарь"
          @tap="goToDetailPage('calendar')"
        />
      </FlexboxLayout>
    </ScrollView>
  </Page>
</template>

<script>
import Calc from "./Calc.vue";
import Converter from "./Converter.vue";
import Calendar from "./Calendar.vue";

export default {
  data() {
    return {};
  },
  methods: {
    goToDetailPage(page) {
      switch (page) {
        case "calc":
          this.$navigateTo(Calc);
          break;
        case "converter":
          this.$navigateTo(Converter);
          break;
        case "calendar":
          this.$navigateTo(Calendar);
          break;
      }
    },
  },
};
</script>

<style scoped>
.kp {
  width: 400px;
  height: 300px;
}
</style>
