<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Task</label>
            <input type="text" name="text" v-model="text" placeholder="Add Task" />
        </div>
        <div class="form-control">
            <label>Day & Time</label>
            <input type="text" name="day" v-model="day" placeholder="Add Day & Time" />
        </div>
        <div class="form-control form-control-check">
            <label>Set Reminder</label>
            <input name="reminder" v-model="reminder" type="checkbox" />
        </div>
        <input type="submit" value="Save Task" class="btn btn-block" />
    </form>
</template>

<script>
export default {
    name: 'AddTask',
    data() {
        return {
            text: '',
            day: '',
            reminder: false
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault();

            if (!this.text) {
                alert('Please add a task');
                return;
            }

            const newTask = {
                id: Math.floor(Math.random() * 10000) + 1,
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }

            this.$emit('add-task', newTask);

            this.text = '';
            this.day = '';
            this.reminder = false;
        },
    },
}
</script>

<style scoped>
.add-form {
    max-width: 500px;
    margin: auto;
    padding: 20px;
}
.add-form .form-control {
    margin-bottom: 10px;
}
.add-form .form-control label {
    display: block;
    text-align: left;
    margin-bottom: 5px;
}
.add-form .form-control input {
    width: 100%;
    padding: 5px;
    border: 1px solid #ccc;
    border-radius: 5px;
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