<template>
  <div class="task-grid">
    <div
      class="task"
      :class="[{'pending': !item.completed}, {'done': item.completed}]"
      v-for="(item,index) in lists"
      :key="index"
    >
      <span @click="removeTaks(index)" class="close">x</span>
      <p @click="change(index)">{{item.name}}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["lists"],
  methods: {
    change(index) {
      this.$emit("changeToCompleted", index);
    },
    removeTaks(i) {
      this.$emit("callRemove", i);
    }
  }
};
</script>

<style>
.task-grid {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  -ms-flex-wrap: wrap;
  flex-wrap: wrap;
}

.task-grid .task {
  margin: 10px;
}

.done {
  color: #ddd;
  border-left: 12px solid #0a8f08;
  background-color: #4caf50;
  text-decoration: line-through;
}

.task {
  position: relative;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  width: 350px;
  height: 150px;
  padding: 10px;
  border-radius: 8px;
  font-size: 2rem;
  font-weight: 300;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
}

.done .close {
  background-color: #0a8f08;
}

.close {
  position: absolute;
  right: 10px;
  top: 10px;
  font-size: 0.9rem;
  font-weight: 600;
  height: 20px;
  width: 20px;
  border-radius: 10px;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
}

.pending .close {
  background-color: #b73229;
}

.pending {
  border-left: 12px solid #b73229;
  background-color: #f44336;
}
</style>
