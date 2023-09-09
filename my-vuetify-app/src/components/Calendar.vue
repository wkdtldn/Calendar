<template>
  <div>
    <v-calendar
      :selected="selectedDate"
      flat
      @click:date="updateSelectedDate"
    ></v-calendar>
    <v-dialog v-model="showEventDialog" max-width="500px">
      <v-card>
        <v-card-title>일정 추가</v-card-title>
        <v-card-text>
          <input class="form-control input"/>
        </v-card-text>
        <v-card-actions>
          <v-btn color="primary" @click="saveEvent">저장</v-btn>
          <v-btn @click="resetEvent">취소</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import { VCalendar } from "v-calendar";

export default {
  name: "CalenderComponent",

  components: {
    VCalendar,
  },
  data() {
    return {
      selectedDate: "", // 선택된 날짜 저장
      showEventDialog: false, // 일정 추가 다이얼로그 표시 여부
      event: {}, // 일정 데이터
    };
  },
  methods: {
    updateSelectedDate(date) {
      this.selectedDate = date;
      this.showEventDialog = true; // 날짜를 선택하면 일정 추가 다이얼로그 표시
    },
    saveEvent() {
      // 일정을 저장하는 로직
      // this.event를 사용하여 선택된 날짜와 추가적인 정보를 처리하고 저장합니다.
      // 저장 후 showEventDialog 변수를 false로 설정하여 다이얼로그를 닫습니다.
      this.showEventDialog = false;
    },
    resetEvent() {
      // 일정 추가 취소 시 실행되는 로직
      // showEventDialog 변수를 false로 설정하여 다이얼로그를 닫습니다.
      this.showEventDialog = false;
    },
  },
};
</script>
<style>
@import "../css/bootstrap.min.css";
</style>
