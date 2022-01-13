<template>
  <div class="container">
    <table class="table is-bordered is-fullwidth mt-6 mb-6">
      <thead>
        <tr>
          <th colspan=3 class="has-background-lightblue">Category</th>
          <th colspan=4 class="has-text-info">{{dataForm.lnkt_maintenancecategorytext}}</th>
          <th colspan=3 class="has-background-lightblue">Type</th>
          <th colspan=3 class="has-text-info">{{dataForm.lnkt_maintenancetypetext}}</th>
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
          <th colspan=3> {{dataForm.lnkt_name}} </th>
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
              <input v-model="this.noCustImpact" type="checkbox" disabled>
              No Customer Impact
            </label>
          </th>
          <th colspan=4> <label class="checkbox">
              <input v-model="dataForm.lnkt_corporateinternet" type="checkbox" disabled>
              Corporate Internet
            </label> </th>
        </tr>
        <tr>
          <th colspan=4>
            <label class="checkbox">
              <input v-model="dataForm.lnkt_fastnetpackages" type="checkbox" disabled>
              Fastnet Packages :
            </label>
          </th>
          <th colspan=5>
            <div class="content">
              <p v-show="this.fastnetPackageLength > 3">*Terlampir pada Fastnet Package Item attachment</p>
              <ul v-show="fastnetPackageLength <= 3 ">
                <li v-for="item, index in dataForm.lnkt_fastnetItem" :key="index"> {{item.lnkt_name}}</li>
              </ul>
            </div>
          </th>


          <th colspan=4> <label class="checkbox">
              <input v-model="dataForm.lnkt_corporatempls" type="checkbox" disabled>
              Corporate MPLS / LC
            </label> </th>
        </tr>
        <tr>
          <th colspan=4>
            <label class="checkbox">
              <input v-model="dataForm.lnkt_homecable" type="checkbox" disabled>
              Home Cable :
            </label>
          </th>
          <th colspan=5> </th>
          <th colspan=4> <label class="checkbox">
              <input v-model="dataForm.lnkt_vod" type="checkbox" disabled>
              VOD
            </label> </th>
        </tr>
        <tr>
          <th colspan=4>
            <label class="checkbox">
              <input v-model="dataForm.lnkt_tvchannel" type="checkbox" disabled>
              TV Channel :
            </label> <br>

          </th>
          <th rowspan=2 colspan=5>
            <div class="content">
              <p v-show="this.tvchannelItemLength > 3">*Terlampir pada TV Channel Item attachment</p>
              <ul v-show="tvchannelItemLength <= 3 ">
                <li v-for="item, index in dataForm.lnkt_tvchannelItem" :key="index"> {{item.lnkt_name}}</li>
              </ul>
            </div>
          </th>
          <th colspan=4> <label class="checkbox">
              <input v-model="dataForm.lnkt_mailservices" type="checkbox" disabled>
              Mail / SMTP Services
            </label> </th>
        </tr>
        <tr>
          <th colspan="1"> <label class="checkbox ml-6">
              <input v-model="dataForm.lnkt_analog" type="checkbox" disabled>
              Analog
            </label></th>
          <th colspan="1">
            <label class="checkbox  ml-2">
              <input v-model="dataForm.lnkt_digital" type="checkbox" disabled>
              Digital
            </label>
          </th>
          <th colspan="1">

            <label class="checkbox  ml-2">
              <input v-model="dataForm.lnkt_sd" type="checkbox" disabled>
              SD
            </label>
          </th>
          <th colspan="1">

            <label class="checkbox  ml-2">
              <input v-model="dataForm.lnkt_hd" type="checkbox" disabled>
              HD
            </label>
          </th>

          <th colspan="4">
            <label class="checkbox">
              <input v-model="dataForm.lnkt_otherproduct" type="checkbox" disabled>
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
            <p :class="{hide: !this.ImpactedAttachment}"> *Terlampir pada attachment</p>
            <div class="columns is-multiline" :class="{hide : this.ImpactedAttachment}">
              <div v-for="item,index in dataForm.getAllImpactedItem" :key="index" class="column">
                <div class="card">
                  <div class="card-content" style="padding:10px;">
                    <div class="content">
                      <p>Type : {{item.lnkt_impacttype}}</p>
                      Impact item : ({{item.lnkt_impact_item.length}})
                      <ol>
                        <li v-for="subitem,index in item.lnkt_impact_item" :key="index"> {{subitem.lnkt_name}}</li>
                      </ol>
                    </div>
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
          <th colspan=5> {{dataForm.lnkt_proposeddate}} </th>
          <th colspan=3> {{dataForm.lnkt_proposedtime}} </th>
          <th colspan=5> {{dataForm.lnkt_justification}}</th>
        </tr>
        <tr class="has-background-lightblue">
          <th colspan=13> 16. Requestor Checklist</th>
        </tr>
        <tr>
          <th colspan=7> <label class="checkbox">
              <input v-model="dataForm.lnkt_contingencyplan" type="checkbox" disabled>
              Contingency Plan / Roll Back Plan
            </label></th>
          <th colspan=6> <label class="checkbox">
              <input v-model="dataForm.lnkt_verificationmethods" type="checkbox" disabled>
              Verification methods
            </label> </th>
        </tr>

        <tr>
          <th colspan=7> <label class="checkbox">
              <input v-model="dataForm.lnkt_approvalcorporate" type="checkbox" disabled>
              Approval from Corporate Customer
            </label></th>
          <th colspan=6> <label class="checkbox">
              <input v-model="dataForm.lnkt_supportingdoc" type="checkbox" disabled>
              Supporting Documents:
            </label> </th>
        </tr>

        <tr>
          <th colspan=7> <label class="checkbox">
              <input v-model="dataForm.lnkt_approvalwp" type="checkbox" disabled>
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
        <tr v-show="picLength  > 3">
          <td colspan="13">*Terlampir pada attachment</td>
        </tr>
        <tr v-show="picLength  <= 3" v-for="item,index in dataForm.lnkt_pic" :key="index">
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
          <th colspan=4> Division Head </th>
        </tr>
        <tr>
          <th colspan=9> 1 or more HUB, FastNet Products, TV Channels, Stock Exchange Members, Axis, more than 1 BDF,
            more than 50 nodes, Apartments, unstandard time.</th>
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

    <div class="pagebreak" :class="{hide: !this.ImpactedAttachment}">
      <table class="table is-bordered is-fullwidth mt-6 mb-6">
        <tr>
          <td colspan=10>
            <p class="mb-3"> *Impacted area attachment</p>
          </td>
        </tr>
        <tr>
          <td>
            <div class="columns is-multiline">
              <div v-for="item,index in dataForm.getAllImpactedItem" :key="index" class="column is-12">
                <div class="card">
                  <div class="card-content" style="padding:10px;">
                    <div class="content">
                      <p><b>Type : {{item.lnkt_impacttype}}</b></p>
                      <div class="columns is-multiline">
                        <div v-for="subitem,index in item.lnkt_impact_item" :key="index" class="column is-3">
                           <div   class="card" >
                        <div class="card-content">
                          {{subitem.lnkt_name}}
                        </div>
                      </div>
                        </div>
                      </div>
                     
                      <!-- <ul>
                        <li> </li>
                      </ul> -->
                    </div>
                  </div>
                </div>
              </div>

            </div>
          </td>
        </tr>
      </table>
    </div>

    <div v-show="this.picLength > 3" class="pagebreak">
      <table class="table is-bordered is-fullwidth mt-6 mb-6">
        <tr>
          <td colspan=10>
            <p class="mb-3"> *Person In Charge for Change Activity attachment </p>
          </td>
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
      </table>
    </div>

    <div v-show="this.fastnetPackageLength > 3" class="pagebreak">
      <table class="table is-bordered is-fullwidth mt-6 mb-6">
        <tr>
          <td colspan=10>
            <p class="mb-3"> *Fastnet package item attachment </p>
          </td>
        </tr>
        <tr>
          <td>
            <div class="columns is-multiline">
              <div v-for="item, index in dataForm.lnkt_fastnetItem" :key="index" class="column is-3">
                <div class="card">
                  <div class="card-content">
                    <div class="content">
                     {{index + 1}}. {{item.lnkt_name}}
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </td>
        </tr>
      </table>
    </div>

     <div v-show="this.tvchannelItemLength > 3" class="pagebreak">
      <table class="table is-bordered is-fullwidth mt-6 mb-6">
        <tr>
          <td colspan=10>
            <p class="mb-3"> *TV channel item attachment </p>
          </td>
        </tr>
        <tr>
          <td>
            <div class="columns is-multiline">
              <div v-for="item, index in dataForm.lnkt_tvchannelItem" :key="index" class="column is-3">
                <div class="card">
                  <div class="card-content">
                    <div class="content">
                     {{index + 1}}. {{item.lnkt_name}}
                    </div>
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
        dataForm: [],
        impactedLength: '',
        ImpactedDetailLength: '',
        ImpactedAttachment: false,
        picLength: '',
        noCustImpact: '',
        fastnetPackageLength: '',
        tvchannelItemLength:''
      }
    },
    async mounted() {
      await this.getDataForm()
      await this.impactedValue()
    },
    methods: {
      async getDataForm() {
        // console.log('get data')
        try {
          await this.$axios.get(
              `http://202.77.101.91:6161/Service1.svc/RCFForReport/${this.$route.params.id}`)
            .then(async res => {
              let rawDataForm = await res.data
              this.dataForm = await rawDataForm[0]
              this.impactedLength = await rawDataForm[0].getAllImpactedItem.length
              this.picLength = await rawDataForm[0].lnkt_pic.length
              this.fastnetPackageLength = await rawDataForm[0].lnkt_fastnetItem.length
              this.tvchannelItemLength = await rawDataForm[0].lnkt_tvchannelItem.length

              if (this.dataForm.lnkt_fastnetpackages == false &&
                this.dataForm.lnkt_homecable == false &&
                this.dataForm.lnkt_tvchannel == false &&
                this.dataForm.lnkt_corporateinternet == false &&
                this.dataForm.lnkt_corporatempls == false &&
                this.dataForm.lnkt_vod == false &&
                this.dataForm.lnkt_mailservices == false &&
                this.dataForm.lnkt_otherproduct == false) {
                this.noCustImpact = true
              }
            })
        } catch (error) {
          console.log(error)
        }
      },

      async impactedValue() {
        let arrDetailLength = []
        let x = this.dataForm
        x.getAllImpactedItem.map(item => {
          arrDetailLength.push(item.lnkt_impact_item.length)
        })
        if (Math.max(...arrDetailLength) > 4) {
          this.ImpactedAttachment = true
        }
      }
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

  .hide {
    display: none !important;
  }

  @media print {
    .pagebreak {
      page-break-before: always;
    }

 
  }

</style>
