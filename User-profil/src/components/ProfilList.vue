<template>
  <div class="container">
    <div class="profile"
          v-for="(profile, index) in profiles"
         :key="index"
         :style="{'background-image':'url('+require('../assets/profil/'+profile.images[0])+')'}"
         @click="setProfile(index)"
    >
      <div  :class="'overlay '+profile.gender">
        <h2>{{profile.name}}</h2>
        <span><i class="fas fa-map-marker-alt"></i>{{profile.location}}</span>
      </div>


    </div>
    <transition name="fade" mode="out-in">
      <profilpage
        v-if="active"
        :profil="activePage"
        @close="closeProfile"
      />
    </transition>



  </div>

</template>
<script>
import profilpage from "./profilpage";
export  default {
  data(){
    return{
      active:false,
      activePage:{},
      profiles:[
        {
          name:"Mike Stand",
          location:"İstanbul, Türkiye",
          description:"Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab at eius error est exercitationem id impedit in inventore ipsum laborum libero magni maxime nesciunt omnis, placeat possimus quasi sapiente veniam.",
          images:[
            'profil_img_4.jpg',
            'profil_img_3.jpg',
            'profil_img_2.jpg',
            'profil_img_1.jpg'
          ],
          like:false,
          gender:"male"

        },
        {
          name:"Jack Pott",
          location:"İstanbul, Türkiye",
          description:"Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab at eius error est exercitationem id impedit in inventore ipsum laborum libero magni maxime nesciunt omnis, placeat possimus quasi sapiente veniam.",
          images:[
            'profil_img_1.jpg',
            'profil_img_2.jpg',
            'profil_img_3.jpg',
            'profil_img_2.jpg',
            'profil_img_1.jpg'
          ],
          like:false,
          gender:"male"

        },
        {
          name:"Olivia",
          location:"İstanbul, Türkiye",
          description:"Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab at eius error est exercitationem id impedit in inventore ipsum laborum libero magni maxime nesciunt omnis, placeat possimus quasi sapiente veniam.",
          images:[
            'profil_img_6.jpg',
            'profil_img_3.jpg',
            'profil_img_2.jpg',
            'profil_img_1.jpg'
          ],
          like:false,
          gender:"famele"

        },
        {
          name:"Liam",
          location:"İstanbul, Türkiye",
          description:"Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab at eius error est exercitationem id impedit in inventore ipsum laborum libero magni maxime nesciunt omnis, placeat possimus quasi sapiente veniam.",
          images:[
            'profil_img_3.jpg',
            'profil_img_6.jpg',
            'profil_img_2.jpg',
            'profil_img_1.jpg'
          ],
          like:false,
          gender:"male"

        }
      ]
    }
  },
  methods:{
    setProfile(index){
      this.activePage = this.profiles[index];
      this.active=true;
    },
    closeProfile(){
      this.active = false;
    }
  },
  components:{
    profilpage
  }
}

</script>
<style scoped lang="scss" >

.container{
  border: 1px solid #111;
  border-radius: 20px;
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
  margin: 0 auto;

    .profile{
      position: relative;
      float: left;
      width: 50%;
      height: 50%;
      background-position: top center;
      background-size: cover;
      cursor: pointer;
    }
  .overlay{
    position: absolute;
    bottom: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 100%;
    height: 20%;
    padding-top: 20px;

    background: linear-gradient(
    to bottom,
    rgba($color: #fff, $alpha:0)0%,
    rgba($color: #fff, $alpha:1)100%,
    );
    h2{
      font-size: 2rem;
      padding:0;
      margin: 0;
    }
    span{
      font-size: 1rem;
      font-weight: bold;
    }
  }
  .male{
    color: #1b404f;
  }
  .famele{
    color:tomato;
  }
  }
.fade-enter, .fade-leave{
  opacity: 0;
}
.fade-enter-active, .fade-leave-active{
  transition: opacity .3s linear;
}


</style>
