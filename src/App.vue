<script setup>
  import DataCard from "../src/components/DataCard.vue"
  import {reactive} from "vue";
  import {onMounted} from "vue";
  import dashboard from '../src/assets/vuesax/linear/vuesax/linear/element-3.svg';
  import settings from  '../src/assets/vuesax/linear/vuesax/linear/setting.svg';
  import search from  '../src/assets/vuesax/linear/vuesax/linear/search-normal.svg';
  import employment from  '../src/assets/vuesax/linear/vuesax/linear/briefcase.svg';
  import talent from  '../src/assets/vuesax/linear/vuesax/linear/user-octagon.svg';
  import activation from  '../src/assets/vuesax/linear/clipboard-tick.svg'
  import global from  '../src/assets/vuesax/linear/vuesax/linear/global.svg';
  import candidate from  '../src/assets/vuesax/linear/vuesax/linear/profile-2user.svg';
  import teacher from  '../src/assets/vuesax/linear/vuesax/linear/teacher.svg';
  import vet from  '../src/assets/vuesax/linear/vuesax/linear/check.svg';
  import profile from '../src/assets/img.png'


  const navs = [
    {name:'Dashboard',icon:dashboard,children:''},
    {name:'System panel',icon:settings,children:[
        {name:'Industry',icon:''},
        {name:'Competency',icon:''},
      ]
    },
    {name:'Finder',icon:search,children:''},
    {name:'Activation',icon:activation,children:''},
    {name:'Vetting',icon:vet,children:''},
    {name:'Employers list',icon:employment,children:''},
    {name:'Talent list',icon:talent,children:''},
    {name:'Global mobility',icon:global,children:''},
    {name:'Candidate',icon:candidate,children:''},
    {name:'Professionals',icon:teacher,children:[
        {name:'Professionals',icon:''},
        {name:'Recruit',icon:''},
      ]},
  ]

  let data2 = [
    {profile:profile,name:'Nancy Tukura', level:'Basic', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {profile:profile,name:'Nancy Tukura', level:'Intermediate', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {profile:profile,name:'Nancy Tukura', level:'Expert', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {profile:profile,name:'Nancy Tukura', level:'Basic', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {profile:profile,name:'Nancy Tukura', level:'Expert', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {profile:profile,name:'Nancy Tukura', level:'Basic', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {profile:profile,name:'Nancy Tukura', level:'Intermediate', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {profile:profile,name:'Nancy Tukura', level:'Expert', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {profile:profile,name:'Nancy Tukura', level:'Basic', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
    {profile:profile,name:'Nancy Tukura', level:'Intermediate', score:'75%', attempt:'3',info:'Rainoil . Warri, Rivers . Full-Time'},
  ]


  const data = reactive({
    dropdown:false,
    active:'all',
    currentPage:1,
    itemPerPage:4,
    icon_to_drop:null,
    isActive:4
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
  <div class="wrapper animate__animated animate__fadeIn">
      <div class="sidebar">
        <div class="logo-div">
          <img src="https://croxxtalent.com/images/logo.png" class="logo" />
        </div>
        <div class="inner-sidebar">
          <div v-for="(i, index) in navs" :key="index" class="nav-items" :class="{'active':i.name === 'Vetting'}">
            <div class="indicator" v-if="data.isActive == index"></div>
            <img :src="i.icon" />
            <div style="width: 100%;">
              <span class="link-name">{{ i.name }}</span>
              <img  @click="data.dropdown = !data.dropdown, handleDropdown(i)" :src="data.dropdown ? '../src/assets/Button/vuesax/linear/vuesax/linear/Vector.svg':'../src/assets/Button/Vector.svg'" v-if="i.children" style="margin-left: 20px" />
              <div v-if="i.children" class="nav-items-children-wrapper-active" :id="i.name">
                <div v-for="j in i.children" class="nav-items-children">
                  <span class="span-link-name">{{j.name}}</span>
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
              <img src="../src/assets/vuesax/linear/message-text.png">
              <img src="../src/assets/vuesax/linear/notification.svg">
            </div>
          </div>
        </div>
        <div class="mid-header">
          <span class="industry">Industry</span>
          <span class="breaker"></span>
          <div>
            <span class="energy_sector">Energy sector </span>
            <img  src="../src/assets/Button/vuesax/linear/vuesax/linear/Vector.svg" />
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
            <div class="chevron"> <img  src="../src/assets/Button/vuesax/bold/vuesax/bold/Vector.svg" />
            </div>
          </div>
        </div>
        <div class="mid-main" v-if="data.active === 'all'">
          <div>
            <data-card v-for="i in paginate(data2)" :profile="i.profile" :key="i.name"  :score="i.score" :Attempt="i.attempt" :name="i.name" :info="i.info" :level="i.level" />
          </div>
          <div>
            <img style="cursor: pointer" @click="previousPage()" :disabled="data.currentPage === 1" class="fa-solid fa-chevron-left" src="../src/assets/Button/Button/Vector.svg" />
            <span style="cursor: pointer" @click="data.currentPage = i" v-for="i in totalPages()" class="pan" :class="{'active_pan':i === data.currentPage}">{{i}}</span>
            <img style="cursor: pointer" @click="nextPage()" :disabled="data.currentPage === totalPages()" src="../src/assets/Button/Vector.svg" />
          </div>
        </div>
      </div>
  </div>
</template>

<style scoped>
*{
  font-family: 'Poppins';
}

.indicator{
  width: 4px;
  height: 32px;
  position: absolute;
  background: #0040A1;
  border-radius: 40px;
  margin-left: -39px;
}

.link-name{
  font-weight: 500;
  font-size: 16px;
  color: #282929;

}
.logo-div{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: start;
  gap: 8px;
  /*border: solid;*/

  width: 228px;
  margin-bottom: 33px;

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

.span-link-name{
  font-weight: 500;
  font-size: 12px;

  color: #282929;
}

.active_pan{
  color: white;
  width: 46px;
  height: 46px;
  background: #0040A1;
  padding: 10px 12px;
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
  width: 92%;
  margin: 20px 45px;
  height: 49px;
  background: #FFFFFF;
  border: 1px solid #C2DBFF;
  border-radius: 20px;

}

.mid-main{
  margin: 40px 45px;
}

.badge-2{
  padding: 8px;
  color: #024f93;
  font-size: 16px;
  line-height: 160%;
  /* identical to box height, or 26px */


  color: #0040A1;
}

.active3{
  width: 120px;
  background: #EBF3FF;
  border-radius: 40px;
  text-align: center;
}

.lower-mid{
  border: 1px solid #C2DBFF;
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
  margin-bottom: -25px;
  color: gray;
}

.active1{
  border-bottom: solid;
  color: black;
}

.breaker{
  width: 2px;
  height: 40px;
  background: #C2DBFF;
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
  background: #FFFFFF;
  /* X Border */
  border-bottom: 1px solid #C2DBFF;

  box-shadow: inset 0px -1px 0px #D6DDEB;

}
.logo{
  width: 164px;
  height: 33px;
}

.sidebar{
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 32px 22px;
  width: 272px;
  border: 1px solid #C2DBFF;
  height: 110vh;
  /* Y Border */

  filter: drop-shadow(1px 0px 0px #D3D6DB);
  border-radius: 0px;
}

.inner-sidebar{
  display: flex;
  flex-direction: column;
  align-items: start;
  width: 272px;
}

.nav-items{
  display: flex;
  flex-direction: row;
  align-items: start;
  padding: 12px 16px;
  gap: 16px;
  width: 224px;
  border-radius: 40px;
  cursor: pointer;
  /*border: solid;*/
}

.active{
  background: #EBF3FF;
  border: 1px solid #C2DBFF;
  border-radius: 40px;
  padding: 12px 16px;
  gap: 16px;

  width: 236px;

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
  border-bottom: solid 1px #C2DBFF;
  width: 92%;
  margin: 10px auto;
  display: flex;
  justify-content: start;
  gap: 20px;
  padding: 10px;
  align-items: center;
}

.route-enter-from{
  opacity: 0;
  /*transform: translateX(100px);*/
}

.route-enter-active{
  transition:all 0.1s linear;
}

.route-leave-to{
  opacity: 0;
  /*transform: translateX(-100px);*/
}
.route-leave-active{
  transition:all 0.1s linear;
}
</style>
