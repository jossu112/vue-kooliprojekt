<template>
    <div class="row m-3">
        <div class="col-12 input-group mb-3">
            <input @keyup.enter="addTODO" class="form-control" type="text" v-model="newTODO">
            <span class="input-group-append">
                <button class="btn btn-secondary" @click="addTODO">Add TODO</button>
            </span>
        </div>
        <div class="col-6">
            <div class="card mb-3">
                <div class="card-header text-white bg-danger">TODO</div>
                <div class="card-body">
                    <ul class="list-group">
                        <li class="list-group-item" v-for="(value, index) in TODOs" :key="index">
                            {{value}}
                            <span
                                @click="markDone(value, index)"
                                class="badge badge-pill badge-success"
                            >
                                done
                            </span>
                            <span
                                @click="removeFromTODOs(index)"
                                class="badge badge-pill badge-danger"
                            >
                                remove
                            </span>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
        <div class="col-6">
            <div class="card mb-3">
                <div class="card-header text-white bg-success">DONE</div>
                <div class="card-body">
                    <ul class="list-group">
                        <li class="list-group-item justify-content-between" v-for="(TODO, index) in done" :key="index">
                            {{TODO.value}}
                            <span
                                class="badge badge-pill badge-danger"
                                @click="removeFromDone(index)"
                            >
                                remove
                            </span>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'ToDo',
  data: function () {
    return {
      newTODO: '',
      TODOs: [],
      done: []
    }
  },
  methods: {
    addTODO () {
      this.TODOs.push(this.newTODO)
      this.newTODO = ''
      console.log(this.TODOs)
    },
    markDone (value, index) {
      this.done.push({value, index})
      this.TODOs.splice(index, 1)
    },
    removeFromTODOs (index) {
      this.TODOs.splice(index, 1)
    },
    removeFromDone (index) {
      this.done.splice(index, 1)
    }
  }
}
</script>
