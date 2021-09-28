<template>
  <router-view/>
  <section>
    <div class="header">
      <div class="new-task">
        <div class="new-task__field">
          <label class="new-task__label" for="newTaskTitle"></label>
          <input
            v-model="newTask.title"
            @keydown.enter="addNewTask"
            class="new-task__input"
            name="newTaskTitle"
            id="newTaskTitle"
            type="text"
            placeholder="Название задачи"
          />
        </div>
        <div class="new-task__field">
          <label class="new-task__label" for="newTaskDescription"></label>
          <input
            v-model="newTask.description"
            class="new-task__input new-task__input_size_small"
            name="newTaskDescription"
            id="newTaskDescription"
            type="text"
            placeholder="Описание"
          />
        </div>
      </div>
      <div class="header__button">
        <button
          @click="addNewTask"
          type="button"
        >
          Добавить
        </button>
      </div>
    </div>
  </section>
  <section class="section">
    <div class="container">
      <div
        v-for="task in tasks"
        :key="task.title"
        @click="editTask = task"
        :class="{ active: editTask === task }"
        class="task"
      >
        <p class="task__title">{{ task.title }}</p>
        <p class="task__description">{{ task.description }}</p>
        <div>
          <button type="button" @click.stop="handleDelete(task)">
            Удалить
          </button>
        </div>
      </div>
    </div>
    <template v-if="editTask">
      <div class="task-editor">
        <div>
          <button @click="editTask = null">Закрыть</button>
          <button
            @click="
              handleDelete(editTask);
              editTask = null;
            "
          >
            Удалить
          </button>
        </div>
        <p class="task__title">{{ editTask.title }}</p>
      </div>
    </template>
  </section>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      newTask: {
        title: "",
        description: "",
      },
      tasks: [
        {
          title: "new Title 1",
          description: "new description",
        },
        {
          title: "new Title 2",
          description: "new description",
        },
        {
          title: "new Title 3",
          description: "new description",
        },
      ],
      editTask: null,
    };
  },

  methods: {
    addNewTask() {
      const newTask = {
        title: this.newTask.title,
        description: this.newTask.description,
      };

      this.tasks.push(newTask);
      this.newTask.title = "";
      this.newTask.description = "";
    },
    handleDelete(taskToRemove) {
      this.tasks = this.tasks.filter((task) => task !== taskToRemove);
    },
  },
};
</script>

<style>
:root {
  /*Fonts*/
  --font-stack: "Montserrat", Arial, sans-serif;

  /*Colors*/
  --text: #394f61;
  --light-text: #7085a5;
}

body,
h1,
p {
  margin: 0;
}

body {
  font-family: var(--font-stack);
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.header {
  display: flex;

  margin: 10px;
}

.header__button {
  margin-left: 10px;
}

.section {
  display: flex;

  padding: 0 15px;
}

.container {
  display: grid;
  grid-gap: 10px;

  width: 100%;
}

.new-task {
  max-width: 400px;

  background-color: #f3f4f6;

  border-radius: 10px;
}

.new-task__input {
  padding: 10px;

  font-size: 20px;

  background-color: #f3f4f6;

  border: 0;
  outline: 0;
}

.new-task__input_size_small {
  font-size: 14px;
}

.task {
  padding: 20px;

  border: 4px solid #e3e4e4;
  border-radius: 10px;
}

.task.active {
  border-color: #7085a5;
}

.task__title {
  margin-bottom: 10px;

  font-weight: 500;
  font-size: 18px;
}

.task__description {
  color: #9e9e9e;

  font-size: 16px;
}

.task-editor {
  width: 600px;

  margin-left: 20px;
  padding: 10px;

  border: 4px solid #7085a5;

  border-radius: 10px;
}
</style>
