<template>
  <div class="p-30 w-screen mx-auto" style="font-family: 'Prompt', sans-serif;">
    <!-- Profile Header -->
    <div class="flex items-center space-x-4 mb-6">
      <img :src="getAvatar(user.avatar)" alt="Avatar" class="w-20 h-20 rounded-full object-cover" />
      <div>
        <h1 class="text-2xl font-bold">{{ user.name }}</h1>
        <p class="text-gray-500 capitalize">{{ user.role }}</p>
      </div>
    </div>

    <div class="mb-6 flex gap-2">
      <input v-model="newTaskTitle" placeholder="Add new task" class="flex-1 border rounded p-2" />
      <button @click="addTask" class="bg-blue-500 text-white px-4 py-2 rounded">Add</button>
    </div>

    <div>
      <h2 class="text-xl font-semibold mb-2">งานของฉัน</h2>
      <ul>
        <li
          v-for="task in tasks"
          :key="task.id"
          class="flex items-center justify-between border-b py-2"
        >
          <div class="flex items-center gap-2">
            <input
              type="checkbox"
              v-model="task.completed"
              @change="updateTaskStatus(task)"
            />
            <span :class="{ 'line-through text-gray-400': task.completed }">
              {{ task.title }}
            </span>
          </div>
          <button @click="deleteTask(task.id)" class="text-red-500">Delete</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {
        name: 'จิรพันธ์ ขุนสันเทียะ',
        role: 'สทท1/1เลขที่3',
        avatar: 'avartar.png'
      },
      newTaskTitle: '',
      tasks: [
        { id: 1, title: 'ทำรายงานประจำเดือน', completed: false },
        { id: 2, title: 'ประชุมงานทีม', completed: true },
        { id: 3, title: 'ตรวจเอกสารโครงการ', completed: false },
      ],
    }
  },
  methods: {
    getAvatar(filename) {
      // ถ้า filename ว่างหรือ null ให้ return ''
      return filename ? `/uploads/${filename}` : '';
    },
    addTask() {
      if (this.newTaskTitle.trim() === '') return;
      this.tasks.push({
        id: Date.now(),
        title: this.newTaskTitle,
        completed: false,
      });
      this.newTaskTitle = '';
    },
    updateTaskStatus(task) {
      // อัปเดตสถานะงาน (ในตัวอย่างนี้ไม่มี backend)
      console.log(`Task ${task.id} status: ${task.completed}`);
    },
    deleteTask(taskId) {
      this.tasks = this.tasks.filter(t => t.id !== taskId);
    }
  }
}
</script>
