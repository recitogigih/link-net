<template>
  <div class="container">
    <p>test </p>
  </div>

</template>


<script>
  export default {

    data() {
      return {

        dataForm: ''


      }
    },
    mounted() {
      this.getDataForm()

    },
    methods: {
      async getDataForm() {
        console.log('get data')
        try {
          await this.$axios.get(
              `http://202.77.101.91:6161/Service1.svc/RCFForReport/${this.$route.params.id}`)
            .then(async res => {
              let rawDataForm = await res.data
              this.dataForm = rawDataForm[0]
              // this.x = dataForm.lnkt_department
              // console.log('Data log', this.dataChart)
            })
        } catch (error) {
          console.log(error)
        }
      },


    }
  }

</script>

<style>
  .has-background-lightblue {
    background: #d6fefe
  }

  .has-background-lightbrown {
    background: #f5d5b8
  }

  .table td,
  .table th {
    border: 1px solid #dbdbdb;
    border-width: 0 0 1px;
    padding: 0.5em 0.75em;
    vertical-align: top;
    font-size: 12px;
  }

</style>
