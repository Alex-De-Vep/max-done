<template>
  <router-view />
  <section>
    <div class="header">
      <div class="new-task">
        <div class="new-task__field">
          <input
            v-model="newTask.title"
            @keydown.enter="addNewTask"
            class="new-task__input"
            name="newTaskTitle"
            id="newTaskTitle"
            type="text"
            placeholder="Название задачи"
            required
          />
        </div>
        <div class="new-task__field">
          <input
            v-model="newTask.description"
            @keydown.enter="addNewTask"
            class="new-task__input new-task__input_size_small"
            name="newTaskDescription"
            id="newTaskDescription"
            type="text"
            placeholder="Описание"
          />
        </div>
      </div>
      <div class="header__button">
        <button @click="addNewTask" type="button">Добавить</button>
      </div>
    </div>
  </section>
  <section class="section">
    <div class="container">
      <div
        v-for="task in tasks"
        :key="task.title"
        @click="editTask = viewEmptyLine(task)"
        :class="{ active: editTask === task }"
        class="task"
      >
        <p class="task__title">{{ task.title }}</p>
        <p v-snip="1" class="task__description" v-if="!task.isDescriptionEmpty">
          {{ task.description }}
        </p>
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
            @click.stop="
              handleDelete(editTask);
              editTask = null;
            "
          >
            Удалить
          </button>
        </div>
        <div class="task-editor__input-wrapper">
          <input v-model="editTask.title" class="task-editor__input" />
        </div>
        <div class="task-editor__textarea-wrapper">
          <textarea
            v-on:focus="removeDefaultText(editTask)"
            placeholder="Добавить описание"
            v-model="editTask.description"
            class="task-editor__textarea"
          />
        </div>
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
        isDescriptionEmpty: false,
      },
      tasks: [
        {
          title: "new Title 1",
          description: "new description",
          isDescriptionEmpty: false,
        },
        {
          title: "new Title 2",
          description: "",
          isDescriptionEmpty: true,
        },
        {
          title: "new Title 3",
          description:
            "Есть много вариантов Lorem Ipsum, но большинство из них имеет не всегда приемлемые модификации, например, юмористические вставки или слова, которые даже отдалённо не напоминают латынь. Если вам нужен Lorem Ipsum для серьёзного проекта, вы наверняка не хотите какой-нибудь шутки, скрытой в середине абзаца. Также все другие известные генераторы Lorem Ipsum используют один и тот же текст, который они просто",
          isDescriptionEmpty: false,
        },
      ],
      editTask: null,
    };
  },

  methods: {
    addNewTask() {
      const newTask = {
        title: this.newTask.title,
        isDescriptionEmpty: this.newTask.description === "",
        description:
          this.newTask.description === ""
            ? (this.newTask.description = "")
            : this.newTask.description,
      };

      if (this.newTask.title === "") {
        return;
      }

      this.tasks.push(newTask);
      this.newTask.title = "";
      this.newTask.description = "";
    },
    handleDelete(taskToRemove) {
      this.tasks = this.tasks.filter((task) => task !== taskToRemove);
    },
    viewEmptyLine(task) {
      if (task.description === "") {
        task.isDescriptionEmpty = false;
        task.description = "Добавить описание";
      }

      if (task && task.isDescriptionEmpty === true) {
        task.isDescriptionEmpty = false;
      }

      return task;
    },
    removeDefaultText(task) {
      if (task.description === "Добавить описание") {
        task.description = "";
        task.isDescriptionEmpty = false;
      }

      return task;
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

body,
input,
textarea {
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
  margin-bottom: 20px;
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

.task__description.hidden {
  display: none;
}

.task-editor {
  width: 600px;
  height: 460px;

  margin-left: 20px;
  padding: 10px;

  border: 4px solid #7085a5;

  border-radius: 10px;
}

.task-editor__input {
  width: 100%;
  max-width: 420px;

  font-weight: 500;
  font-size: 16px;

  padding: 10px;

  background-color: #f3f4f6;

  border: 0;
  border-radius: 10px;

  outline: 0;
}

.task-editor__textarea {
  width: 100%;
  max-width: 420px;
  height: 180px;

  padding: 10px;

  background-color: #f3f4f6;

  border: 0;
  border-radius: 10px;

  outline: 0;

  resize: none;
}

.task-editor__input,
.task-editor__textarea-wrapper {
  margin-top: 20px;
}

</style>
