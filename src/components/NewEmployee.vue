<template>
  <div id="new-employee">
    <div class="row">
      <form @submit.prevent="saveEmployee" class="col s12">
        
        <div class="row">
          <div class="field col s12">
            <input type="text" v-model="employee_id" required>
            <label>Employee ID#</label>
          </div>
        </div>

        <div class="row">
          <div class="field col s12">
            <input type="text" v-model="name" required>
            <label>Name</label>
          </div>
        </div>

        <div class="row">
          <div class="field col s12">
            <input type="text" v-model="dept" required>
            <label>Deparment</label>
          </div>
        </div>

             <div class="row">
          <div class="field col s12">
            <input type="text" v-model="position" required>
            <label>Potision</label>
          </div>
        </div>
  <button class="btn" type="submit">submit</button>
     <router-link to="/" class="btn grey">Cancel</router-link>
      </form>
    </div>

    </div>
</template>

<script>
import db from './firebaseInit'
export default {
  name : 'new-employee',
  data () {
      return {
          employee_id: null,
          name: null,
          dept: null,
          position: null
      }
  },
  methods: {
    saveEmployee () {
      db.collection('employees').add({
        employee_id: this.employee_id,
        name: this.name,
        dept: this.dept,
        position: this.position
      }).then(docRef => {
        this.$router.push('/')
      })
      .catch(error => {
        console.log(error)
      })
    }
  }
}
</script>

