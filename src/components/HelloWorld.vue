<template>
  <div class="hello">
    <!-- khusus v-on bisa diganti dengan @ ,
     referensinya cari di shorthand nya-->    

    <input 
      type="text" 
      placeholder="nama depan"
      v-model="firstname">
    <input 
      type="text" 
      placeholder="nama belakang"
      v-model="lastname">
    <br>
    <button @click="showName()">Tampilkan data diri</button>  

    <div v-if="isNameShown">
      <h1>Halo nama saya {{ firstname }} {{lastname}}</h1>
      <p>
        Saya tingal di {{address.city}}, {{address.province}}
        umur {{ getMyAge }}
      
      </p>
      <p v-if="age >0 && age <10">saya masih kecil</p>
      <p v-else-if="age >10 && age <=20">saya masih remaja</p>
      <p v-else>saya udah dewasa</p>
      <p>Saya {{ work ? "Bekerja" : "Tidak Bekerja"}}</p>
      <h2>Social Media</h2>
      <ul>
        <li>
        <!-- khusus untuk binding data v-bind bisa diganti dengan :-->
          <a
            v-bind:href="facebookUrl" 
            target="_blank"
            :title ="work ? 'Bekerja' : 'Tidak Bekerja'"
          >
            Facebook
          </a>
        </li>
        <!-- khusus untuk binding data -->
        <li>
          <a
            :href="twitterUrl"
            target="_blank"
          >
            Twitter
          </a>
          <button v-on:click="showPopUp(true)">Pop Up</button>
        </li>
      </ul>

    </div>
    <ul>
      <li v-for="pemain in daftarPemain" :key="pemain.id">
        {{pemain.namaPemain}}
      </li>
    </ul>
    <p>{{ getAddress}}</p>
    <h2>Raw HTML</h2>
      <button :disabled="buttonState">Klik me</button>
      <p>Using mustaches: {{ rawHtml }}</p>
  <p>Using v-html directive: <span v-html="rawHtml"></span></p>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      firstname: "Ade",
      lastname: "Pranaya",
      age: 20,
      work: false,
      address: {
        city: "Manggar",
        province: "Bangka Belitung"
      },
      facebookUrl: "https://www.facebook.com/ade.pranaya",
      twitterUrl: "https://twitter.com/adepranaya1",
      rawHtml: "<strong>WOw</strong>",
      buttonState: true,
      isNameShown: false,
      daftarPemain: [
        { id: 1, namaPemain: "Messi" },
        { id: 2, namaPemain: "Ronaldo" },
        { id: 3, namaPemain: "Depran" }
      ]
    };
  },
  methods: {
    showPopUp(condition) {
      if (condition) {
        let { city, province } = this.address;
        alert("Hello " + city);
      } else {
        alert("wow");
      }
    },
    showName() {
      this.isNameShown = !this.isNameShown;
    }
  },
  computed: {
    getMyAge() {
      return new Date().getFullYear() - 1998;
    },
    getAddress() {
      let { city, province } = this.address;
      return city + " " + province;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
