<template>
  <div class="clientslist">
    <div class="main-wrapper">
       <main-header></main-header>
      <sidebar></sidebar>
      <!-- Page Wrapper -->

      <div class="page-wrapper">
      
        <!-- Page Content -->

        <div class="content container-fluid">
        
        <clientsheader />  
          
        <clientsfilter /> 
          

          <div class="row">
            <div class="col-md-12">
              <div class="table-responsive">
                <table class="table table-striped custom-table datatable" id="clientlist">
                  <thead>
                    <tr>
                      <th>Name</th>
                      <th>Client ID</th>
                      <th>Contact Person</th>
                      <th>Email</th>
                      <th>Mobile</th>
                      <th>Status</th>
                      <th class="text-end">Action</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="item in clientlist" :key="item.id">
                      <td>
                        <h2 class="table-avatar">
                          <router-link to="/client-profile" class="avatar"><img :src="loadImg(item.image)" alt=""></router-link>
                          <router-link to="/client-profile">{{item.name}}</router-link>
                        </h2>
                      </td>
                      <td>{{item.clientid}}</td>
                      <td>{{item.contactperson}}</td>
                      <td>{{item.email}}</td>
                      <td>{{item.mobile}}</td>
                      <td>
                        <div class="dropdown action-label">
                          <a href="javascript:void(0)" class="btn btn-white btn-sm btn-rounded dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false"><i class="fa fa-dot-circle-o text-success"></i> {{item.status}} </a>
                          <div class="dropdown-menu">
                            <a class="dropdown-item" href="javascript:void(0)"><i class="fa fa-dot-circle-o text-success"></i> Active</a>
                            <a class="dropdown-item" href="javascript:void(0)"><i class="fa fa-dot-circle-o text-danger"></i> Inactive</a>
                          </div>
                        </div>
                      </td>
                      <td class="text-end">
                        <div class="dropdown dropdown-action">
                          <a href="javascript:void(0)" class="action-icon dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false"><i class="material-icons">more_vert</i></a>
                          <div class="dropdown-menu dropdown-menu-right">
                            <a class="dropdown-item" href="javascript:void(0)" data-bs-toggle="modal" data-bs-target="#edit_client"><i class="fa fa-pencil m-r-5"></i> Edit</a>
                            <a class="dropdown-item" href="javascript:void(0)" data-bs-toggle="modal" data-bs-target="#delete_client"><i class="fa fa-trash-o m-r-5"></i> Delete</a>
                          </div>
                        </div>
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
            </div>
          </div>

        </div>
        <!-- /Page Content -->
      
        <clientsmodal />
        
      </div>
      <!-- /Page Wrapper -->
    </div>
  </div>
</template>
<script>
import clientlist from '../../../assets/json/clientlist.json';
import util from '../../../assets/utils/util'
const images = require.context('../../../assets/img/profiles', false, /\.png$|\.jpg$/)
  import Vue from 'vue'
  export default {
     data() {
    return {
      clientlist: clientlist
    }
    },
    components: {
   
    },
    mounted() {
    util.datatable('#clientlist')
    },
     methods: {
        loadImg(imgPath) {
            return images('./' + imgPath).default
    },
    },
    name: 'clientslist'
  }
</Script>