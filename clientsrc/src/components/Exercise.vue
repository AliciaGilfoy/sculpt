<template>
  <div>
    <div class="title-row col-12">
      <h3>
        <u contenteditable @blur="onEdit('title', exerciseData._id)">{{exerciseData.title}}</u>
      </h3>
      <p
        v-if="myWorkouts"
        @click="deleteExerciseFromWorkout(exerciseData)"
        class="deletebutton text-danger"
      >X</p>
      <p v-if="myExercises" @click="deleteExercise(exerciseData)" class="deletebutton text-danger">X</p>
    </div>
    <h4 class="col-12" v-show="exerciseData.sets">
      Sets-
      <span contenteditable @blur="onEdit('sets', exerciseData._id)">{{exerciseData.sets}}</span>
    </h4>
    <h4 class="col-12" v-show="exerciseData.reps">
      Reps-
      <span contenteditable @blur="onEdit('reps', exerciseData._id)">{{exerciseData.reps}}</span>
    </h4>
    <h4 class="col-12">
      Weight-
      <span
        contenteditable
        @blur="onEdit('weight', exerciseData._id)"
      >{{exerciseData.weight}}</span>
    </h4>
    <h4 class="col-12" v-show="exerciseData.distance">
      Distance-
      <span
        contenteditable
        @blur="onEdit('distance', exerciseData._id)"
      >{{exerciseData.distance}}</span>
    </h4>
    <h4 class="col-12" v-show="exerciseData.time">
      Time-
      <span contenteditable @blur="onEdit('time', exerciseData._id)">{{exerciseData.time}}</span>
    </h4>
  </div>
</template>

<script>
export default {
  name: "Exercise",
  props: ["exerciseData"],
  computed: {
    myWorkouts() {
      return this.$route.path === "/myworkouts";
    },
    myExercises() {
      return this.$route.path === "/myexercises";
    }
  },
  methods: {
    deleteExercise(data) {
      this.$store.dispatch("deleteExercise", data._id);
    },
    deleteExerciseFromWorkout(exerciseData) {
      let data = {
        workoutId: this.$store.state.activeWorkout.id,
        exerciseId: exerciseData._id
      };
      this.$store.dispatch("deleteExerciseFromWorkout", data);
    },
    onEdit(where, exerciseId) {
      let workoutId = this.$store.state.activeWorkout._id;
      if (workoutId) {
        if (where == "reps") {
          let data = { reps: event.target.innerText * 1 };
          console.log(data);
          this.$store.dispatch("editWorkoutExercise", {
            update: data,
            workoutId: workoutId,
            exerciseId: exerciseId
          });
        } else if (where == "sets") {
          let data = { sets: event.target.innerText * 1 };
          console.log(data);
          this.$store.dispatch("editWorkoutExercise", {
            update: data,
            workoutId: workoutId,
            exerciseId: exerciseId
          });
        } else if (where == "title") {
          let data = { title: event.target.innerText };
          console.log(data);
          this.$store.dispatch("editWorkoutExercise", {
            update: data,
            workoutId: workoutId,
            exerciseId: exerciseId
          });
        } else if (where == "weight") {
          let data = { weight: event.target.innerText * 1 };
          console.log(data);
          this.$store.dispatch("editWorkoutExercise", {
            update: data,
            workoutId: workoutId,
            exerciseId: exerciseId
          });
        } else if (where == "distance") {
          let data = { distance: event.target.innerText * 1 };
          console.log(data);
          this.$store.dispatch("editWorkoutExercise", {
            update: data,
            workoutId: workoutId,
            exerciseId: exerciseId
          });
        } else if (where == "time") {
          let data = { time: event.target.innerText * 1 };
          console.log(data);
          this.$store.dispatch("editWorkoutExercise", {
            update: data,
            workoutId: workoutId,
            exerciseId: exerciseId
          });
        }
      } else if (!workoutId) {
        if (where == "reps") {
          let data = { reps: event.target.innerText * 1 };
          console.log(data);
          this.$store.dispatch("editExercise", {
            update: data,
            exerciseId: exerciseId
          });
        } else if (where == "sets") {
          let data = { sets: event.target.innerText * 1 };
          console.log(data);
          this.$store.dispatch("editExercise", {
            update: data,
            exerciseId: exerciseId
          });
        } else if (where == "title") {
          let data = { title: event.target.innerText };
          console.log(data);
          this.$store.dispatch("editExercise", {
            update: data,
            exerciseId: exerciseId
          });
        } else if (where == "weight") {
          let data = { weight: event.target.innerText * 1 };
          console.log(data);
          this.$store.dispatch("editExercise", {
            update: data,
            exerciseId: exerciseId
          });
        } else if (where == "distance") {
          let data = { distance: event.target.innerText * 1 };
          console.log(data);
          this.$store.dispatch("editExercise", {
            update: data,
            exerciseId: exerciseId
          });
        } else if (where == "time") {
          let data = { time: event.target.innerText * 1 };
          console.log(data);
          this.$store.dispatch("editExercise", {
            update: data,
            exerciseId: exerciseId
          });
        }
      }
    }
  }
};
</script>

<style scoped>
.listItem {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  position: relative;
  background-color: transparent;
  align-items: baseline;
}
.title-row {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
</style>