<template>
  <div id="User">
    <h2>
      Hola <span> {{ username }}, </span> ¡Bienvenido!
    </h2>
    <p> su correo es {{email}}</p>
  </div>
</template>





<script>
// export default {
//   name: "User",
//   data: function () {
//     return {
//       username: "none",
//     };
//   },
//   created: function () {
//     this.username = this.$route.params.username;
//   },
// };
</script>


<script>
import axios from "axios";
export default {
  name: "User",
  data: function () {
    return {
      username: "",
      emai: "",
      dob: ""
    };
  },
  created: function () {
    this.username = this.$route.params.username;
    console.log(this.$route);
    let self = this;
    axios
      .get("http://127.0.0.1:8000/user/info/" + this.username)
      .then((result) => {
        self.email = result.data.email;
        self.dob = result.data.dob;
        console.log(self.dob);
      })
      .catch((error) => {
        alert("ERROR Servidor");
      });
  },
};
</script>





<style>
#User {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
#User h2 {
  font-size: 50px;
  color: #283747;
}
#User span {
  color: crimson;
  font-weight: bold;
}
</style>