<template>
  <div
    class="flex flex-col p-3 w-full h-full items-center justify-center gap-3 bg-slate-200"
  >
    <h1
      class="flex flex-col w-full h-20 justify-center items-center bg-slate-300 text-xl font-bold"
    >
      인생 달력
    </h1>
    <div class="flex gap-3">
      <input
        class="w-[10rem] p-2 border-black rounded-md"
        placeholder="생년월일을 입력하세요"
        type="date"
        min="0"
        v-model="birthDate"
      />
      <button
        class="w-[4rem] bg-red-400 text-white border rounded-md border-black"
        @click="calculateAge"
      >
        입력
      </button>
    </div>
    <div
      class="p-4 flex flex-col items-center w-full h-full bg-slate-100"
    >
      🥳만 나이: {{ userAgeInfo.age }} 세 <br />
      🥳 살아온 주: {{ userAgeInfo.weeks }} 주 <br />
      🥳 살아온 일: {{ userAgeInfo.days }} 일 <br />
    </div>
  </div>
</template>
  
<script setup lang="ts">
type IUserAgeInfo = {
  age: number
  weeks: number
  days: number
  daysUntilBirthday: number
};

const birthDate = ref<string>("");
const userAgeInfo = ref<IUserAgeInfo>({
  age: 0,
  weeks: 0,
  days: 0,
  daysUntilBirthday: 0,
});

const calculateAge = () => {
  if (birthDate.value) {
    const birth = new Date(birthDate.value);
    const today = new Date();

    let calculatedAge = today.getFullYear() - birth.getFullYear();
    const monthDifference = today.getMonth() - birth.getMonth();

    if (
      monthDifference < 0 ||
      (monthDifference === 0 && today.getDate() < birth.getDate())
    ) {
      calculatedAge--;
    }

    const oneDay = 24 * 60 * 60 * 1000; // 밀리초 단위의 하루
    const totalDays = Math.round((today.getTime() - birth.getTime()) / oneDay);
    const totalWeeks = Math.floor(totalDays / 7);

    const nextBirthday = new Date(today.getFullYear(), birth.getMonth(), birth.getDate())
    if (today > nextBirthday) {
      nextBirthday.setFullYear(today.getFullYear() + 1)
    }
    const daysUntilBirthday = Math.round((nextBirthday.getTime() - today.getTime()) / oneDay)


    userAgeInfo.value = {
      age: calculatedAge,
      weeks: totalWeeks,
      days: totalDays,
      daysUntilBirthday,
    };
  } else {
    console.log("생년월일을 입력하세요.");
  }
};
</script>
  
  <style>
</style>