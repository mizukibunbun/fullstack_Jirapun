<template>
   <div class="min-h-screen flex flex-col items-center justify-center  text-center px-4" style="font-family: 'Prompt', sans-serif;">
    <!-- เนื้อหา -->
    <main class="w-full  px-2 py-2 bg-white mt-6 rounded-none shadow-none pt-24 ">
      <h2 class="text-xl font-semibold mb-4 text-gray-800">ยินดีต้อนรับเข้าสู่ระบบประเมินบุคลากร</h2>
      <p class="text-gray-600">
        ระบบนี้ถูกออกแบบมาเพื่อให้ผู้บริหารและบุคลากรสามารถประเมินผลการปฏิบัติงานได้อย่างสะดวก
        สามารถกรอกแบบประเมิน ดูรายงาน และสรุปผลคะแนนได้ในที่เดียว
      </p>
 <button
      @click="Profile"
      class="px-6 py-2 bg-blue-600 text-white rounded hover:bg-blue-700 transition">
      Go Profile
 </button>
       
    </main>
  </div>
</template>

<script>
import ProfilePage from '../pages/ProfilePage.vue';
export default {
  name: 'Main',
  methods: {
    Profile() {
      this.$router.push('/Profile');
    }
  }
};
</script>
