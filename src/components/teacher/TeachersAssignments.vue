<template>
  <div class="h-dvh w-screen bg-gray-100" style="font-family: 'Prompt', sans-serif;">
    <TeacherForm
      :teacher="teacher" 
      :criteria="criteria" 
      @save-draft="saveDraft" 
      @submit-evaluation="submitEvaluation" 
    />
  </div>
</template>

<script>
import TeacherForm from "../../views/teacherFrom.vue"
// สมมติว่า jsonData เป็นไฟล์ JSON ที่มีโครงสร้างตามที่ใช้ใน data()
import jsonData from "../../resource/criteria.json"

export default {
  name: "TeachersAssignments",

  components: {
    TeacherForm, // ต้องประกาศคอมโพเนนต์ที่ใช้งาน
  },

  data() {
    return {
      teacher: jsonData.teacher, 
      criteria: jsonData.criteria, 
    };
  },

  methods: {
    // ฟังก์ชันสำหรับบันทึกแบบร่าง
    saveDraft(data) {
      console.log("บันทึกร่าง:", data);
      // ... โค้ดสำหรับบันทึกแบบร่าง
    },

    // ฟังก์ชันสำหรับส่งการประเมิน
    submitEvaluation(data) {
      console.log("ส่งผลประเมิน:", data);
      // ... โค้ดสำหรับส่งการประเมิน
    },
  },
};
</script>