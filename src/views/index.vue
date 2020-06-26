<template>
  <div class="nixom">

<!-- Footer Navbar -->
    <div>
      <b-navbar toggleable="lg" type="dark" variant="primary" fixed="bottom">
        <b-container>
          <!-- Right aligned nav items -->
          <b-navbar-nav class="mr-auto ml-auto">
            <b-navbar-nav>
              <b-nav-item >
                <a href="https://www.dammyton.netlify.app">
                Designed and Developed by
                <i style="font-size:10px" class="fa fa-copyright ml-1"></i> Dammyton</a>
              </b-nav-item>
            </b-navbar-nav>
          </b-navbar-nav>
        </b-container>
      </b-navbar>
    </div>


<!-- Celebrant's Picture -->
<div class="bg">
</div>

<!-- Birthday Wish Form -->
    <div id="contact">
      <!-- <div>
      <label>Search:
        <input
            type="text"
            v-model="commentText"
            v-on:keyup.enter="addComment" />
      </label>
      <h5>Results: <small>{{results.count}}</small></h5>
      <ul>
        <li v-for="result in results" :key="result">
          {{result.commentText}}
        </li>
        <li>{{results}}</li>
      </ul>
      </div>
      -->

      <b-container>
        <h6 class="text-center mt-3 pb-5">Birthday Wishes</h6>
        <b-row>
          <b-col md="2"></b-col>
          <b-col md="8">
            <b-form>
              <b-form-group label="Message">
                <textarea v-model="commentText" rows="4" required class="form-control"></textarea>
              </b-form-group>

              <center>
                <!-- <button class="mt-1 send" type="submit">Send</button> -->
                <span>
                  <input class="mt-1 send" @click="addComment()" type="submit" value="submit" />
                </span>
              </center>
            </b-form>
          </b-col>
          <b-col md="2"></b-col>
        </b-row>
      </b-container>
    </div>
    <hr />

<!--Birthday Wishes List -->
    <div id="pricing">
      <b-container>
        <b-row class="mt-3" v-for="result in results.slice().reverse()" :key="result">
          <b-col md="2"></b-col>
          <b-col md="8">
            <b-card-group>
              <b-card class="dsh">
                <p style="color:#00d0ff;font-weight:bold">
                  Birthday wishes to olamilekan
                  <img
                    src="../assets/birthday.png"
                    alt="user"
                    width="20px"
                    height="20px"
                    align="center"
                  />
                </p>
                <b-card-text style="color:#fff">{{result.commentText}}</b-card-text>
              </b-card>
            </b-card-group>
          </b-col>
          <b-col md="2"></b-col>
        </b-row>
      </b-container>
    </div>
  </div>
</template>


<script>
import axios from "axios";

export default {
  data() {
    return {
      form: {
        email: "",
        message: ""
      },
      commentText: "",
      results: [],
      show: true
    };
  },
  created() {
    let uri = `https://5e97081077f543001633903f.mockapi.io/birthday/comments`;
    axios.get(uri).then(response => {
      //console.log(response.data,'created')
      this.results = response.data;
    });
  },
  methods: {
    addComment() {
      let today = new Date().toLocaleDateString();
      console.log(today, "mytoday");

      let newComment = {
        commentText: this.commentText
      };
      console.log(newComment);

      axios
        .post(
          "https://5e97081077f543001633903f.mockapi.io/birthday/comments",
          newComment
        )
        .then(response => {
          console.log(response, "Successful");
          //  res.json(response)
          return (this.commentText = " " && window.location.reload());

          //  router.push("/")
        })
        .catch(error => {
          console.log(error);
        });
    },
    reload() {
      return window.location.reload();
    }
  }
};
</script>
<style scoped>

a{
  color: #ffffff !important;
  background-color: none !important;
}
a:hover{
  color:#c8c5cb;
}
.bg{
     background: url('../assets/ddd.png');
    background-repeat: no-repeat;
    background-size: contain;
    background-attachment: fixed;
    background-position: inherit;
    height:650px;
    width: 100%
}
.phaybg {
  background: #01b5ff;
}
.get {
  color: #ffffff;
}
.get:hover {
  color: #007bff;
  background: #ffffff;
  border: 1px solid #007bff;
}
.nixom {
  padding-bottom: 60px;
}
.name {
  font-size: 10px;
  font-family: serif;
}
.nav-item,
.nav-link {
  font-size: 12px;
  color: #ffffff !important;
}
.nav-link:hover {
  color: rgba(255, 255, 255, 0.5) !important;
}

.nav-link:active,
.nav-link:focus {
  color: #9c27b0 !important;
}

a.active {
  color: orange;
}
legend {
  color: #c8c5cb !important;
}
/* .welcome {
  background: url('../assets/wave.png');
  width: auto;
  height: 600px;
  background-position: center;
  background-size: cover;
} */
.well {
  background: linear-gradient(
    to top,
    #007bff,
    #00d0ff,
    #00d0ff,
    #007bff,
    #007bff
  );
  /* background: url('../assets/bl.png'); */
  width: auto;
  height: 650px;
  background-position: left;
  background-size: cover;
  color: #fff;
  background-attachment: fixed;
}
#services {
  padding-top: 120px;
  padding-bottom: 80px;
}
#portfolio {
  padding-top: 80px;
  padding-bottom: 80px;
}
#pricing {
  padding-top: 20px;
  padding-bottom: 40px;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
#contact {
  padding-top: 10px;
}
a {
  color: #007bff;
  text-decoration: none;
}
.col-md-3,
.col-sm-6 {
  width: auto;
}
.services_hd {
  color: #01b5ff;
  font-size: 15px;
  padding: 7px;
}
.services_ic {
  color: #01b5ff;
  font-size: 40px;
}
.services_cont {
  font-size: 12px;
}
i {
  font-size: 28px;
}
p.card-text {
  margin-bottom: 0px;
}
.material-icons.md-36 {
  font-size: 36px;
}
.material-icons.md-12 {
  font-size: 12px;
  color: #ffffff;
}

.des {
  font-size: 18px;
}

.dsh {
  border-radius: 0px 30px 0px 30px;
  background: #007bff;
}





 @media(max-width:420px){
    .bg{
     background: url('../assets/ddd.png');
    background-repeat: no-repeat;
    background-size: contain;
    background-attachment: fixed;
    background-position: inherit;
    height:220px;
    width: 100%;
}
 }

</style>
