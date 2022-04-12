<template>
  <div class="profile">
    <h1>Beer App</h1>
    <div class="person">
        <img v-bind:src="picture">
        <h2 class="person-name">{{firstName}}</h2>
        <p class="age">{{age}}</p>
        <p class="post">{{post}}</p>
        <button @click="getUser()" id="user-button">Get Random User</button>
    </div>
  </div>
 
</template>

<script>
export default {
  name: 'Profile',
  components: {
   
  },
  data() {
    return {
      firstName: 'John',
      picture: 'https://randomuser.me/api/portraits/men/0.jpg',
      age: '20',
      post: 'name',
    }
  },
  
  methods: {
    getDate(date_of_birth){
        let now = new Date(); //Текущя дата
        let today = new Date(now.getFullYear(), now.getMonth(), now.getDate()); //Текущя дата без времени
        let dobFilter = date_of_birth.replace(/[^0-9,.]/g, ', ')
        let dob = new Date(dobFilter); //Дата рождения
        let dobnow = new Date(now.getFullYear(), dob.getMonth(), dob.getDate()); //ДР в текущем году
        let age;
        age = today.getFullYear() - dob.getFullYear();
        if (today < dobnow) {
          return age = age-1;
        }else{
          return age
        }
    },
    async getUser() {
      const res = await fetch('https://random-data-api.com/api/users/random_user')
      const results = await res.json()
      this.firstName = results.first_name;
      this.age = this.getDate(results.date_of_birth);
      this.picture = results.avatar;
      this.post = results.employment.title;
    }
  },
  beforeMount(){
    this.getUser()
 },
}

</script>

<style>
.profile{
    width: 40%;
    height: 100%;
    background-color: #301B28;
    color: #fff;
}
.person{
    margin: 40px auto;
}
.person img{
    width: 50%;
    border-radius: 100%;
}
#user-button{
  padding: 15px 25px;
  background-color: transparent;
  font-weight: 600;
  font-size: 1rem;
  color: #fff;
  border: 3px solid rgb(248, 248, 248);
  transition: all 0.2s ease-in-out;

}
#user-button:hover{
  background-color: #654358;
  
}
@media (max-width: 800px) {
  .profile{
    width: 100%;

  }
}


</style>