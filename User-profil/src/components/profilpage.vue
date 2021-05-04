<template>
  <div class="containerr" :style="{'background-image':'url('+require('../assets/profil/'+activeImg)}">
    <div :class="'overlay-gradient '+profil.gender">
      <div class="back">
        <i class="fas fa-angle-left" @click="closeProfile"></i>
      </div>
      <div class="actions">
        <i class="far fa-heart" v-if="!profil.like" @click="profil.like =! profil.like"></i>
        <i class="fas fa-heart red" v-if="profil.like" @click="profil.like =! profil.like"></i>
      </div>
      <div class="overlay">
        <h2>{{ profil.name }}</h2>
        <span><i class="fas fa-map-marker-alt"></i>{{ profil.location }}</span>
        <p>{{ profil.description }}</p>
      </div>
      <div class="gallery">
        <div class="gallery-image"
             :class="{'inactiy':activeImg !== image}"
             v-for="(image, index) in profil.images"
             :key="index"
        >
          <img :src="require('../assets/profil/'+ image)"
               @click="activeImg = image"
               alt="">


        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: [
    'profil'
  ],
  data() {
    return {
      activeImg: ''
    }
  },
  methods: {
    closeProfile() {
      this.$emit("close");
    }
  },
  beforeMount() {
    this.activeImg = this.profil.images[0];
    console.log(this.activeImg)
  }
}
</script>
<style lang="scss" scoped>
.containerr {
  position: relative;
  width: 100%;
  height: 100vh;
  background-position: top center;
  background-size: cover;
  transition: .4s all linear;

  .overlay-gradient {
    width: 100%;
    height: calc(100vh - 20px);
    padding-top: 20px;

    .overlay {
      position: absolute;
      bottom: 0;
      width: calc(100% - 40px);
      padding: 100px 20px 10px;
      color: #fff;

      h2 {
        font-size: 3rem;
      }

      span {
        font-size: 1rem;
      }

      p {
        font-size: 1.1rem;
        padding: 0 0 4.5rem 0;
      }
    }


  }

  .gallery {
    position: absolute;
    bottom: 0;
    display: flex;
    align-items: center;
    justify-content:space-between;
    width: 100%;
    height: 10%;

    .gallery-image {
      width: 80px;
      height: 80px;
      border-radius: 50px;
      overflow: hidden;
      cursor: pointer;
      box-shadow: 0 15px 30px rgba(0, 0, 0, .2),
      0 10px 20px rgba(0, 0, 0, .2);
      transition: trasform .2s linear;

      img {
        max-width: 80px;
        height: auto;
      }
    }
    .inactiy{
      opacity: .7;
      box-shadow: none;
      transition: trasform .2s linear;
    }


  }

  .famele {
    background: linear-gradient(
        to bottom,
        rgba($color: #fff, $alpha: 0) 30%,
        rgba($color: #Ac2a1b, $alpha: 1) 90%,
        rgba($color: #dd5f15, $alpha: 1) 100%
    )
  }

  .male {
    background: linear-gradient(
        to bottom,
        rgba($color: #fff, $alpha: 0) 30%,
        rgba($color: #1bac83, $alpha: 1) 90%,
        rgba($color: #15dddd, $alpha: 1) 100%
    )

  }

  .actions {
    position: absolute;
    right: 0;
    top: 0;
    padding: 20px;

    .red {
      color: #Ac2a1b;
    }

    i {
      font-size: 3rem;
      cursor: pointer;
      color: #Ac2a1b;
    }
  }

  .back {
    position: absolute;
    left: 0;
    top: 0;
    padding: 10px;

    i {
      font-size: 25px;
    }
  }


}

</style>
