<template>
  <form @submit="submitTask" action="" class="add-form">
    <div class="form-control">
      <label for="title">Task Title</label>
      <input v-model="title" id="title" type="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label for="time">Day & Time</label>
      <input v-model="day" id="time" type="date" placeholder="Add Day & Time" />
    </div>
    <div class="form-control form-control-check">
      <label for="reminder">Set Reminder</label>
      <input v-model="reminder" id="reminder" type="checkbox" />
    </div>
    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "addTaskForm",
  data() {
    return {
      title: "",
      day: "",
      reminder: false,
    };
  },
  methods: {
    submitTask(e) {
      e.preventDefault();
      if (!this.title) {
        alert("Please Add Task title");
        return;
      }
      const newTask = {
        id: Math.floor(Math.random() * 100000),
        text: this.title,
        day: this.day,
        reminder: this.reminder,
      };

      this.$emit("add-task", newTask);
      this.title = "";
      this.day = "";
      this.reminder = false;
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>
