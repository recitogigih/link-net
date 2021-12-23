<template>
  <div class="container">
    <table class="table is-bordered is-fullwidth mt-6 mb-6">
      <thead>
        <tr>
          <th colspan=3 class="has-background-lightblue">Category</th>
          <th colspan=4 class="has-text-info">Improvement</th>
          <th colspan=3 class="has-background-lightblue">Type</th>
          <th colspan=3 class="has-text-info">Activation</th>

        </tr>
      </thead>
      <tbody>
        <tr>
          <th colspan=3> <img src="/linknet-logo.png" style="width:100px;" /> </th>
          <td colspan=9></td>
          <td><b><i>LN-09-27</i></b></td>
        </tr>
        <tr>
          <th colspan=14>
            <center>Request for Change Form</center>
          </th>
        </tr>
        <tr class="has-background-lightblue">
          <th colspan=3> 1. Change # </th>
          <th colspan=2> 2. Requested by </th>
          <th colspan=2> 3. Department </th>
          <th colspan=3> 4. Division </th>
          <th> 5. Request Date </th>
          <th colspan=2> 6. Change Category </th>
        </tr>
        <tr>
          <th colspan=3> {{dataForm.lnkt_changecategory}} </th>
          <th colspan=2> {{dataForm.lnkt_requestbyid}} </th>
          <th colspan=2> {{dataForm.lnkt_department}} </th>
          <th colspan=3> {{dataForm.lnkt_division}} </th>
          <th> {{dataForm.lnkt_requestdate}} </th>
          <th colspan=2>
            {{dataForm.lnkt_changecategory}} <br>
           
          </th>
        </tr>
        <tr class="has-background-lightblue">
          <th colspan=7> 7. Project Name </th>
          <th colspan=6> 8. Reason of Change </th>
        </tr>
        <tr>
          <th colspan=7> {{dataForm.lnkt_projectname}}</th>
          <th colspan=6> {{dataForm.lnkt_reasonofchange}} </th>
        </tr>
        <tr class="has-background-lightblue">
          <th colspan=13> 9. Summary Description of Change and expected output </th>
        </tr>
        <tr>
          <th colspan=13> {{dataForm.lnkt_summarydescription}} </th>
        </tr>
        <tr class="has-background-lightblue">
          <th colspan=13> 10. Product / Service Impact </th>
        </tr>
        <tr>
          <th colspan=9>
            <label class="checkbox">
              <input type="checkbox">
              No Customer Impact
            </label>
          </th>
          <th colspan=4> <label class="checkbox">
              <input v-model="dataForm.lnkt_corporateinternet" type="checkbox">
              Corporate Internet
            </label> </th>
        </tr>
        <tr>
          <th colspan=4>
            <label class="checkbox">
              <input v-model="dataForm.lnkt_fastnetpackages" type="checkbox">
              Fastnet Packages :
            </label>
          </th>
          <th colspan=5> .. </th>


          <th colspan=4> <label class="checkbox">
              <input v-model="dataForm.lnkt_corporatempls" type="checkbox">
              Corporate MPLS / LC
            </label> </th>
        </tr>
        <tr>
          <th colspan=4>
            <label class="checkbox">
              <input v-model="dataForm.lnkt_homecable" type="checkbox">
              Home Cable :
            </label>
          </th>
          <th colspan=5> .. </th>
          <th colspan=4> <label class="checkbox">
              <input v-model="dataForm.lnkt_vod" type="checkbox">
              VOD
            </label> </th>
        </tr>
        <tr>
          <th colspan=4>
            <label class="checkbox">
              <input v-model="dataForm.lnkt_tvchannel" type="checkbox">
              TV Channel :
            </label> <br>

          </th>
          <th colspan=5> .. </th>
          <th colspan=4> <label class="checkbox">
              <input type="checkbox">
              Mail / SMTP Services
            </label> </th>
        </tr>
        <tr>
          <th colspan="1"> <label class="checkbox ml-6">
              <input type="checkbox">
              Analog
            </label></th>
          <th colspan="1">
            <label class="checkbox  ml-2">
              <input type="checkbox">
              Digital
            </label>
          </th>
          <th colspan="1">

            <label class="checkbox  ml-2">
              <input type="checkbox">
              SD
            </label>
          </th>
          <th colspan="1">

            <label class="checkbox  ml-2">
              <input type="checkbox">
              HD
            </label>
          </th>
          <th colspan="5">..</th>
          <th colspan="4">
            <label class="checkbox">
              <input type="checkbox">
              Others: All Fastnet Internet service
            </label>
          </th>
        </tr>
        <tr class="has-background-lightblue">
          <th colspan=13> 11. Impact Type (Lost all Service, Degradation, etc) </th>
        </tr>
        <tr>
          <th colspan=13> {{dataForm.lnkt_impacttype}} </th>
        </tr>
        <tr class="has-background-lightblue">
          <th colspan=13> 12. Impacted Area (HUB, Node, Building, BDF, Corporate Customer, Axis/NTS Links) </th>
        </tr>
        <tr>
          <th colspan=13>
            <div v-show="this.impactedLength < 15" class="columns is-multiline">
              <div v-for="item,index in dataForm.getAllImpactedItem" :key="index" class="column is-3">
                <div class="card">
                  <div class="card-content" style="padding:10px;">
                    <p>{{item.lnkt_name}}</p>
                  </div>
                </div>
              </div>
            </div>
          </th>
        </tr>
        <tr class="has-background-lightbrown">
          <th colspan=13> CHANGE DATE & TIME </th>
        </tr>
        <tr>
          <th colspan=13> Standard time windows for Change Activity: </th>
        </tr>
        <tr>
          <th colspan=5 class="has-background-lightblue"> 13. Proposed Date </th>
          <th colspan=3 class="has-background-lightblue"> 14. Proposed Time </th>
          <th colspan=5 class="has-background-lightblue"> 15. Justification for unstandard time</th>
        </tr>
        <tr>
          <th colspan=5> {{dataForm.lnkt_targetclosed}} </th>
          <th colspan=3> {{dataForm.lnkt_targetclosed}} </th>
          <th colspan=5> {{dataForm.lnkt_justification}}</th>
        </tr>
        <tr class="has-background-lightblue">
          <th colspan=13> 16. Requestor Checklist</th>
        </tr>
        <tr>
          <th colspan=7> <label class="checkbox">
              <input v-model="dataForm.lnkt_contingencyplan" type="checkbox">
              Contingency Plan / Roll Back Plan
            </label></th>
          <th colspan=6> <label class="checkbox">
              <input v-model="dataForm.lnkt_verificationmethods" type="checkbox">
              Verification methods
            </label> </th>
        </tr>

        <tr>
          <th colspan=7> <label class="checkbox">
              <input v-model="dataForm.lnkt_approvalcorporate" type="checkbox">
              Approval from Corporate Customer
            </label></th>
          <th colspan=6> <label class="checkbox">
              <input v-model="dataForm.lnkt_supportingdoc" type="checkbox">
              Supporting Documents:
            </label> </th>
        </tr>

        <tr>
          <th colspan=7> <label class="checkbox">
              <input v-model="dataForm.lnkt_approvalwp" type="checkbox">
              Approval or WP from Axis / NTS
            </label></th>
          <th colspan=6> </th>
        </tr>

        <tr class="has-background-lightblue">
          <th colspan=13> 17. Person In Charge for Change Activity</th>
        </tr>
        <tr>
          <th colspan=1> No </th>
          <th colspan=4> Name </th>
          <th colspan=4> Mobile Phone</th>
          <th colspan=4> Email</th>
        </tr>
        <tr v-for="item,index in dataForm.lnkt_pic" :key="index">
          <th colspan=1> {{index+1}} </th>
          <th colspan=4> {{item.lnkt_name}} </th>
          <th colspan=4> {{item.lnkt_phonenumber}}</th>
          <th colspan=4> {{item.emailaddress}}</th>
        </tr>
        <tr class="has-background-lightbrown">
          <th colspan=13> AUTHORIZATION </th>
        </tr>
        <tr class="has-background-lightblue">
          <th colspan=9> Impact </th>
          <th colspan=4> Authorization Level </th>
        </tr>
        <tr>
          <th colspan=9> Less than 50 nodes. </th>
          <th colspan=4> Division Head  </th>
        </tr>
        <tr>
          <th colspan=9> 1 or more HUB, FastNet Products, TV Channels, Stock Exchange Members, Axis, more than 1 BDF, more than 50 nodes, Apartments, unstandard time.</th>
          <th colspan=4> Director </th>
        </tr>
        <tr class="has-background-lightblue">

          <th colspan=4> 18. Requested By: </th>
          <th colspan=4> 19. Acknowledge by:</th>
          <th colspan=5> 20. Approved by:(Division Head / Director)</th>
        </tr>
        <tr>
          <th colspan=4> <br><br> </th>
          <th colspan=4> <br><br> </th>
          <th colspan=5> <br><br> </th>
        </tr>
        <tr>
          <th colspan=1> Name: </th>
          <th colspan=3> {{dataForm.lnkt_requestbyid}}</th>
          <th colspan=1> Name: </th>
          <th colspan=3> {{dataForm.lnkt_1stapprovalid}}</th>
          <th colspan=1> Name: </th>
          <th colspan=4> {{dataForm.lnkt_2ndapprovalid}} </th>
        </tr>
        <tr>
          <th colspan=1> Date: </th>
          <th colspan=3> {{dataForm.lnkt_requestdate}}</th>
          <th colspan=1> Date: </th>
          <th colspan=3> {{dataForm.lnkt_1stapproveddate}}</th>
          <th colspan=1> Date: </th>
          <th colspan=4> {{dataForm.lnkt_2ndapproveddate}}</th>
        </tr>

        <tr class="has-background-lightbrown">
          <th colspan=13> VERIFICATION (to be filled by NOC) </th>
        </tr>
        <tr class="has-background-lightblue">
          <th colspan=4>21. Completion Date & Time </th>
          <th colspan=4>22. Verification Remarks</th>
          <th colspan=5>23. Acknowledge (NOC Spv.)</th>
        </tr>

        <tr class="">
          <th colspan=4>{{dataForm.lnkt_validationdate}} </th>
          <th colspan=4>{{dataForm.lnkt_troubleticketid}}</th>
          <th colspan=5>{{dataForm.lnkt_validationby}}</th>
        </tr>



      </tbody>
    </table>

    <div v-show="this.impactedLength > 15" class="pagebreak">
      <table class="table is-bordered is-fullwidth mt-6 mb-6">

        <tr>
          <td>
            <p class="mb-3"> Impacted area attachment </p>
            <div class="columns is-multiline">
              <div v-for="item,index in dataForm.getAllImpactedItem" :key="index" class="column is-3">
                <div class="card">
                  <div class="card-content" style="padding:10px;">
                    <p>{{item.lnkt_name}}</p>
                  </div>
                </div>
              </div>
            </div>
          </td>
        </tr>
      </table>

    </div>
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
              this.impactedLength = rawDataForm[0].getAllImpactedItem.length
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

  @media print {
    .pagebreak {
      page-break-before: always;
    }

    /* page-break-after works, as well */

  }

</style>
