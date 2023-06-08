<script setup>
  import DataCard from "../src/components/DataCard.vue"
  import {reactive} from "vue";
  import {onMounted} from "vue";

  const navs = [
    {name:'Dashboard',icon:'fa-solid fa-border-all',children:''},
    {name:'System panel',icon:'fa-solid fa-gear',children:[
        {name:'Industry',icon:''},
        {name:'Competency',icon:''},
      ]
    },
    {name:'Finder',icon:'fa-solid fa-magnifying-glass',children:''},
    {name:'Activation',icon:'fa-regular fa-paste',children:''},
    {name:'Vetting',icon:'fa-solid fa-shield-cat',children:''},
    {name:'Employers list',icon:'fa-solid fa-briefcase',children:''},
    {name:'Global mobility',icon:'fa-solid fa-globe',children:''},
    {name:'Candidate',icon:'fa-solid fa-user-group',children:''},
    {name:'Professionals',icon:'fa-solid fa-graduation-cap',children:[
        {name:'Professionals',icon:''},
        {name:'Recruit',icon:''},
      ]},
  ]

  let data2 = [
    {name:'Nancy Tukura', level:'Basic', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {name:'Nancy Tukura', level:'Intermediate', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {name:'Nancy Tukura', level:'Expert', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {name:'Nancy Tukura', level:'Basic', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {name:'Nancy Tukura', level:'Expert', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {name:'Nancy Tukura', level:'Basic', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {name:'Nancy Tukura', level:'Intermediate', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {name:'Nancy Tukura', level:'Expert', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {name:'Nancy Tukura', level:'Basic', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {name:'Nancy Tukura', level:'Intermediate', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
  ]


  const data = reactive({
    dropdown:false,
    active:'all',
    currentPage:1,
    itemPerPage:4,
    icon_to_drop:null
  })

  const paginate = (arr) => {
    let arr_length_split = arr.length/2
    let start = (data.currentPage - 1) * data.itemPerPage
    let end = start + data.itemPerPage
    return arr?.slice(start ? start : 0, end ? end : arr_length_split)
  }

  const elipses = (value) => {
    if (value)
        return value
      else if (value <= 14)
        return value
      else
        return value.substr(0, )+`...${value}`
  }


  const totalPages = () => {
    return Math.ceil(Number(data2.length) / Number(data.itemPerPage));
  }

  const nextPage = () => {
    if (data.currentPage < totalPages()) {
      data.currentPage++;
    }
  }

  const previousPage = () => {
    if (data.currentPage > 1) {
      data.currentPage--;
    }
  }

  const handleDropdown = (x) => {
    const dropdown = document.getElementById(`${x.name}`)
    if(data.dropdown){
      dropdown.classList.add('nav-items-children-wrapper')
      dropdown.classList.remove('nav-items-children-wrapper-active')
    }else{
      dropdown.classList.add('nav-items-children-wrapper-active')
      dropdown.classList.remove('nav-items-children-wrapper')
    }
  }
</script>

<template>
  <div class="wrapper">
      <div class="sidebar">
        <div class="inner-sidebar">
          <img src="https://croxxtalent.com/images/logo.png" class="logo" />

          <div v-for="i in navs" :key="i" class="nav-items" :class="{'active':i.name === 'Vetting'}">
            <i :class="i.icon"></i>
            <div>
              <span>{{ i.name }}</span>
              <i  @click="data.dropdown = !data.dropdown, handleDropdown(i)" :class="data.dropdown ? 'fa-solid fa-chevron-down':'fa-solid fa-chevron-up'" v-if="i.children" style="margin-left: 20px"></i>
              <div v-if="i.children" class="nav-items-children-wrapper-active" :id="i.name">
                <div v-for="j in i.children" class="nav-items-children">
                  <span>{{j.name}}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="main">
        <div class="top-header">
          <div class="top-header-inner">
            <h3 class="system-panel">System Panel</h3>
            <div class="top-header-icon-area">
              <i class="fa-regular fa-message"></i>
              <i class="fa-regular fa-bell"></i>
            </div>
          </div>

        </div>
        <div class="mid-header">
          <span class="industry">Industry</span>
          <span class="breaker"></span>
          <div>
            <span class="energy_sector">Energy sector </span>
            <i  class="fa-solid fa-chevron-down"></i>
          </div>
        </div>
        <div class="lower-mid">
          <span class="badge-2 active3">Well Service</span>
          <span class="badge-2">Well Service</span>
          <span class="badge-2">Well Service</span>
          <span class="badge-2">Well Service</span>
          <span class="badge-2">Well Service</span>
          <span class="badge-2">Well Service</span>
          <span class="badge-2">Well Service</span>
        </div>
        <div class="lower-mid-nav-2">
          <span @click="data.active = 'all'"  class="item" :class="{'active1':data.active === 'all'}">All</span>
          <span @click="data.active = 'Stimulation Equipment'" class="item" :class="{'active1':data.active === 'Stimulation Equipment'}">Stimulation Equipment</span>
          <span @click="data.active = 'Auxiliary Equipment'" class="item" :class="{'active1':data.active === 'Auxiliary Equipment'}">Auxiliary Equipment</span>
          <span @click="data.active = 'Cementing Equipment'" class="item" :class="{'active1':data.active === 'Cementing Equipment'}">Cementing Equipment</span>
          <span @click="data.active = 'Down-holes tools'" class="item" :class="{'active1':data.active === 'Down-holes tools'}">Down-holes tools</span>
          <span @click="data.active = 'Pressure jobs'" class="item" :class="{'active1':data.active === 'Pressure jobs'}">Pressure jobs</span>
          <div class="navi">
            <div class="chevron"> <i  class="fa-solid fa-chevron-left" style="color: white;"></i></div>
            <div class="chevron"><i  class="fa-solid fa-chevron-right" style="color: white"></i></div>
          </div>
        </div>
        <div class="mid-main" v-if="data.active === 'all'">
          <div>
            <data-card v-for="i in paginate(data2)" :key="i.name"  :score="i.score" :Attempt="i.attempt" :name="i.name" :info="i.info" :level="i.level" />
          </div>
          <div>
            <i @click="previousPage()" :disabled="data.currentPage === 1" class="fa-solid fa-chevron-left"></i>
            <span @click="data.currentPage = i" v-for="i in totalPages()" class="pan" :class="{'active_pan':i === data.currentPage}">{{i}}</span>
            <i @click="nextPage()" :disabled="data.currentPage === totalPages()" class="fa-solid fa-chevron-right"></i>
          </div>
        </div>
      </div>
  </div>
</template>

<style scoped>
.system-panel{

}
.navi{
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
}

.pan{
  padding: 10px;
  border-radius: 10px;
  margin: 5px;

}

.industry{
  font-weight: 900;
  font-size: 20px;
}

.active_pan{
  background-color: #111178;
  color: white;

}

.energy_sector{
  font-size:14px;
  margin-right: 10px;
}
.chevron{
  background-color: rgba(62, 51, 51, 0.91);
  width: 12px;
  height: 12px;
  border-radius: 360px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 5px;
}

.lower-mid-nav-2{
  display: flex;
  align-items: center;
  justify-content: start;
  gap: 50px;
  width: 90%;
  border: solid .5px;
  padding: 8px;
  border-radius:10px;
  margin: 20px 45px;
}

.mid-main{
  margin: 40px 45px;
}

.badge-2{
  padding: 8px;
  border-radius: 20px;
  font-size: 14px;
  color: #024f93;
}

.active3{
  background: rgba(36, 87, 188, 0.15);
}

.lower-mid{
  border: solid .5px;
  width: 80%;
  margin: 20px 45px;
  padding: 15px;
  border-radius: 20px;
  display: flex;
  justify-content: space-between;
}

.item{
  font-size: 12px;
  margin-left: 20px;
  padding-bottom: 5px;
  cursor: pointer;
  margin-bottom: -15px;
  color: gray;


}

.active1{
  border-bottom: solid;
  color: black;
}

.breaker{
  border: solid rgba(36, 87, 188, 0.99) .5px;
  height: 30px;
}

.top-header-icon-area{
  display: flex;
  gap: 30px;
  align-items: center;
  justify-content: center;
}
.wrapper{
  display: flex;
}

.system-panel{
  font-size: 28px;
}

.top-header-inner{
  width: 90%;
  /*border: solid crimson;*/
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.top-header{
  display: flex;
  align-items: center;
  justify-content: center;
  /*border: solid;*/
  width: 100%;
  border-bottom: solid .5px ;
}
.logo{
  width: 150px;
  margin-bottom: 20px;
  margin-top: 20px;
}
.sidebar{
  border-right:solid .5px;
  width: 250px;
  height: 110vh;
}
.inner-sidebar{
  /*border: solid;*/
  display: flex;
  flex-direction: column;
  gap: 15px;
  margin-left: 20px;
  transform: scale(.98);
}

.nav-items{
  display: flex;
  align-items: start;
  justify-content: start;
  gap: 15px;
  /*border: solid;*/
  font-size: 14px;
  /*padding: 10px;*/


}

.active{
  background: rgba(36, 87, 188, 0.09);
  border-radius: 30px;
  height: 30px;
  display: flex;
  justify-content: start;
  align-items: center;
  padding-left: 5px;


}
.nav-items-children{
  margin-bottom: 12px;
  margin-top: 12px;
  font-size: 12px;
  font-weight: 400;
  transition: .5s linear;

}

.nav-items-children-wrapper{
  /*border: solid;*/
  height: 0;
  opacity: 0 !important;
  transition: .2s linear;
  display: flex;
  align-items: center;

}
.nav-items-children-wrapper-active{
  /*border: solid;*/
  height: 50px;
  flex-direction: column;
  opacity: 1;
  transition: .2s linear;
  display: flex;
  align-items: start;
  justify-content: start;
  margin-bottom: 20px;

}

.main{
  width: 100%;
  height: 100vh;
}

.mid-header{
  border-bottom: solid .5px rgba(36, 87, 188, 0.99);
  width: 92%;
  margin: 10px auto;
  display: flex;
  justify-content: start;
  gap: 20px;
  padding: 10px;
  align-items: center;
}
</style>
