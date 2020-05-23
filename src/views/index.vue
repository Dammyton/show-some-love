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
                <a href="https://www.platiniumnets.xyz">
                Designed and Developed by
                <i style="font-size:10px" class="fa fa-copyright ml-1"></i> platiniumnets</a>
              </b-nav-item>
            </b-navbar-nav>
          </b-navbar-nav>
        </b-container>
      </b-navbar>
    </div>


<!-- Celebrant's Picture -->
<div class="bg">
  <!-- <center>
    <img
                          src="../assets/IMG-20191031-WA0006.jpg"
                          alt="user"
                          width="150px"
                          height="150px"
                          class="rounded-circle mt-5"
                        />
  </center> -->
</div>

<!--
    <div class="well">
      <b-container-fluid>
        <b-row style="margin-left:0px;margin-right: 0; !important;">
          <b-col sm="3" md="3"></b-col>

          <b-col sm="6" md="6" style="padding:100px 0px;">
            <div class="text-center">
              <span style="font-family:'Noto sans',serif;font-size:50px ">Hi,</span>
              <h4 style="font-family:'Noto sans'">I'm DAMILOLA OWOLABI</h4>
            </div>
            <div>
              <center>
                <b-card style="width:75%">
                  <b-container>
                    <b-row>
                      <b-col md="4" sm="4">
                        <img
                          src="../assets/lekan-birthday.png"
                          alt="user"
                          width="150px"
                          height="150px"
                          class="rounded-circle"
                          align="center"
                        />
                      </b-col>
                      <b-col md="8" sm="8">
                        <p
                          class="mt-3"
                          style="color:#007bff;margin-bottom: 0.01rem;"
                        >Software Developer</p> -->
                        <!-- <p>Software Developer</p>
                          <p>Wordpress Developer</p>
                        <p>JavaScript Geek</p>-->
                        <!-- <p
                          style="
                        margin-bottom: 0.01rem;
                        color:#3e5569;
                        font-size:12px;
                        font-family:'Noto sans',sans-seriff
                        "
                        >JavaScript Geek</p>
                        <i style="color:#007bff; font-size:10px" class="fa fa-map-marker"></i>
                        <span
                          style="color:#3e5569;
                        font-size:12px;
                        font-family:'Noto sans',sans-seriff"
                        >Lagos, Nigeria.</span>
                        <br />
                        <p style="margin-top: 1rem;margin-bottom:0">
                          <a class="btn btn-primary btn-sm get" href="#portfolio">Get Started</a>
                        </p>
                      </b-col>
                    </b-row>
                  </b-container>
                </b-card>
              </center>
            </div>
          </b-col>
          <b-col class="welcome" sm="3" md="3"></b-col>
        </b-row>
      </b-container-fluid>
    </div>
    -->

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
    // search: function() {
    //   axios
    //     .post(`https://birthday-app.free.beeceptor.com/comments`)
    //     // .post(`https://5e97081077f543001633903f.mockapi.io/birthday/birthday.io`)
    //     .then(response => {
    //       console.log(response.data,"birthday")
    //       res.json(response)
    //       this.results = response.data;
    //     });

    //     axios
    //     .get(`https://birthday-app.free.beeceptor.com/comments`)
    //     // .post(`https://5e97081077f543001633903f.mockapi.io/birthday/birthday.io`)
    //     .then(response => {
    //       console.log(response.data,"birthday")
    //       res.json(response)
    //       this.results = response.data;
    //     });
    // }
  }
};
</script>
<style scoped>
/* @media (min-width: 300px) {
  .welcome{
  background: url('../assets/wave.png');
  width: auto;
  height: 300px;
  background-position: center;
}
.well { */
/* background: linear-gradient(to top, #bec8ca, #00d0ff); */
/* width: auto;
  height: 350px;
  background-position: center;
  position: relative;
  color: #fff;
  background: linear-gradient(to top, #86b2e0, #007bff);
  background-attachment: fixed;
}
}
@media (min-width: 300px) {
  img{
  width: 50px;
  height: 50px;
}
.ful{
  width:20px;
}
}*/
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
.dshh {
  border-radius: 0px 30px 0px 30px;
  width: 90%;
  /* height: 280px; */
}
.dshhh {
  border-radius: 0px 30px 0px 30px;
  width: 90%;
  /* height: 375px; */
}
.dsh2 {
  border-radius: 0px 30px 0px 30px;
  padding: auto;
  height: 40px;
  width: 120px;
  background-color: #01b5ff;
  color: white;
}
.dsh2 > div.card-body {
  padding: 10px 0;
}
.dsh3 {
  border-radius: 50%;
  height: 80px;
  width: 80px !important;
}
.dsh4 {
  border-radius: 0px 40px 0px 40px;
  width: 100%;
  height: 70px;
}
.myuser {
  font-size: 40px;
}
.name {
  font-size: 24px;
}
.fa-connectdevelop {
  font-size: 18px;
  font-weight: 900;
}
.send {
  color: #fff;
  background: #007bff;
  padding: 5px 20px;
  border-radius: 20px;
  border-color: #007bff;
  display: inline-block;
  user-select: none;
  font-size: 1rem;
  font-weight: 700;
  text-align: center;
  vertical-align: middle;
  text-transform: uppercase;
}
.send:hover {
  background: #ffffff;
  color: #007bff;
  border: 1px solid #007bff;
}
.quote {
  color: #fff;
  background: #01b5ff;
  padding: 5px 20px;
  border-radius: 20px;
  border-color: #01b5ff;
  display: inline-block;
  user-select: none;
  font-size: 10px;
  font-weight: 700;
  text-align: center;
  vertical-align: middle;
  text-transform: uppercase;
}
.quote:hover {
  background: #ffffff;
  color: #01b5ff;
  border: 1px solid #01b5ff;
}
.quote2 {
  color: #fff;
  background: orange;
  padding: 5px 20px;
  border-radius: 20px;
  border-color: orange;
  display: inline-block;
  user-select: none;
  font-size: 10px;
  font-weight: 700;
  text-align: center;
  vertical-align: middle;
  text-transform: uppercase;
}
.quote2:hover {
  background: #ffffff;
  color: orange;
  border: 1px solid orange;
}
.quote3 {
  color: #fff;
  background: darkcyan;
  padding: 5px 20px;
  border-radius: 20px;
  border-color: darkcyan;
  display: inline-block;
  user-select: none;
  font-size: 10px;
  font-weight: 700;
  text-align: center;
  vertical-align: middle;
  text-transform: uppercase;
}
.quote3:hover {
  background: #ffffff;
  color: darkcyan;
  border: 1px solid darkcyan;
}
.visit {
  color: #fff;
  background: #007bff;
  padding: 5px 17px;
  border-radius: 20px;
  border-color: #007bff;
  display: inline-block;
  user-select: none;
  font-size: 9px;
  font-weight: 500;
  text-align: center;
  vertical-align: middle;
  text-transform: uppercase;
}
.visit:hover {
  background: #ffffff;
  color: #007bff;
  border: 1px solid #007bff;
}
h6 {
  font-weight: 900;
  font-size: 25px;
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
    /* -webkit-animation: mymove 5s infinite; */ /*Chrome, Safari, Opera */
   /* animation: mymove 5s infinite;*/
}
 }

/* Chrome, Safari, Opera */
/* @-webkit-keyframes mymove {
    from {background:  url('../assets/ddd.png');}
    to {background: url('../assets/IMG-20191031-WA0006.jpg')}
} */

/* Standard syntax */
/*@keyframes mymove {
    from {background:  url('../assets/ddd.png');}
    to {background:  url('../assets/IMG-20191031-WA0006.jpg');}
}


*/
</style>
