<template>

<body>

<div id="app">
  <!--
  <ul>
    <li v-for="data in records">
      {{ data.id }} <br>
      {{ data.first_release_date }} <br>
      {{ data.name }} <br>
      {{ data.rating }} <br>
      {{ data.summary }} <br>
    </li>
  </ul>
  -->

  <div class="header" style="text-align:left;">
      <div style="opacity: 0.2;font-weight:bold; font-family: 'Montserrat', sans-serif;">VIDEO</div>
              <div class="childClass firstchild" style="top:75px;margin-left:110px; font-family: 'Montserrat', sans-serif;">
                  Video Games
              </div>
  </div>


  <div class="row">

      <div class="rightcolumn" style="border:0px dotted red; padding:20px;">
            <div class="form2" style="padding:20px;background-color: #0e1a2b;">
              <div style="font-weight:bold; font-family: 'Montserrat', sans-serif;">Filter Results</div>
              <br>
              <form>
                  <label>Name (contains)</label>
                  <input type="text" placeholder="Text string" style="width:100%;">
                  <br><br>
                  <label>Minimum Score</label>
                  <input type="text" placeholder="1 - 10" style="width:100%;">
                  <br><br>
                  <label>Order by</label>
                    <div class="container_order_by">
                        <div class="arrow_up" style="text-align:center;">
                          <button style="float:right;font-family: 'Montserrat', sans-serif; font-size: 10px; background: #5692e8; color: #ffffff; width:20px;"> &nbsp; </button>
                        </div>
                        <div class="select_order">
                            <select style="width:100%;">
                                <option selected>Release date</option>
                                <option>Score</option>
                                <option>Name</option>
                            </select>
                        </div>
                    </div>
                    <br>
                    <button style="float:right;font-family: 'Montserrat', sans-serif; font-size: 10px; background: #5692e8; color: #ffffff; padding:5px;">Clear</button>   
                    <br>
               </form>
            </div>
            
      </div> <!-- END rightolumn -->


      <div class="leftcolumn">

          <div class="card" v-for="post in posts" :key="post.id" style="padding-top:0px;padding-left:0px;padding-bottom:0px;">
          
              <div class="container2" style="border:0px dotted green;">
                <div class="badge2">
                    <div class="circle">
                        <span class="circle-content">9</span>
                    </div>
                </div>
                <div class="img2">
                  &nbsp;
                </div>
                <div class="text2">
                    <div class="content" style="height:172px;padding:20px;border:0px solid yellow; overflow:hidden;">
                      <div style="font-weight:bold; font-family: 'Montserrat', sans-serif;">
                        {{ post.name }}
                      </div>
                      <div>
                        Release date : {{ post.first_release_date }}
                      </div>
                      <br>
                      <div>
                        {{ post.summary }}
                      </div>
                    </div>
                    <div class="mobile-spacer" style="width:100%;border:0px solid red;">
                      &nbsp;
                    </div>
                </div>
                
              </div>

          </div> <!-- END card -->

      </div> <!-- END leftcolumn -->


  </div> <!-- END row -->



</div>

</body>

</template>



<script>
export default {
  data() {
    return {
      posts: []
    };
  },
  methods: {
    fetchPosts() {
      fetch("http://localhost/applicant_test.json")
        .then(response => response.json())
        .then(data => (this.posts = data));
    }
  },
  mounted() {
    this.fetchPosts();
  }
};
</script>


<style>
    
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@100&display=swap');
  /*
  font-family: 'Montserrat', sans-serif;
  */

  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@100&family=Mulish:wght@200&display=swap');
  /*
  font-family: 'Mulish', sans-serif;
  */

  * {
    box-sizing: border-box;
  }

  /* Add a gray background color with some padding */
  body {
    font-family: 'Mulish', sans-serif;
    font-size:10px;
    padding: 20px;
    background: #f1f1f1;
    background-image: linear-gradient(to bottom, #081221, #03080f);
    color: #ffffff;
  }

  input, select{
    font-family: 'Montserrat', sans-serif;
    font-size: 10px;
    background: #182c47;
    color: #ffffff;
  }

  button{
    font-family: 'Montserrat', sans-serif;
    font-size: 10px;
    background: #5692e8;
    color: #ffffff;
  }
  

  /* Header/Blog Title */
  .header {
    padding: 30px;
    font-size: 40px;
    text-align: center;
    opacity: 0.3;
  }
  
  /* Create two unequal columns that floats next to each other */
  /* Left column */
  .leftcolumn {   
    float: left;
    width: 75%;
  }
  
  /* Right column */
  .rightcolumn {
    float: left;
    width: 25%;
    padding-left: 20px;
  }
  
  /* Fake image */
  .fakeimg {
    background-color: #aaa;
    width: 100%;
    padding: 20px;
  }
  
  /* Add a card effect for articles */
  .card {
     background-color: #0e1a2b ;
     padding: 20px;
     margin-top: 20px;
  }
  
  /* Clear floats after the columns */
  .row:after {
    content: "";
    display: table;
    clear: both;
  }
  
  /* Footer */
  .footer {
    padding: 20px;
    text-align: center;
    background: #ddd;
    margin-top: 20px;
  }
  
  .container2{
        width: 100%;
      height: 200px;
        border: 0px solid black;
  }
      
  .img2{
      width: 25%;
      height: 100%;
      background-color: #03080f;
      float: left;
  }
       
  .text2{
      width: 65%;
      height: 100%;
        float: left;
  }
  
  .badge2{
      height: 100%;
        float: right;
  }
  
  .badge2-mobile{
      height: 100%;
      background-color: yellow;
        float: right;
  }
  
  .circle {
    display: inline-table;
    vertical-align: middle;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    margin-top:80px;
    font-family: 'Montserrat', sans-serif;
    font-size: 10px;
    background: #5692e8;
    color: #ffffff;
  }

  
  .circle-content {
    display: table-cell;
    vertical-align: middle;
    text-align: center;
  }
  
  .container_order_by{
      width: 100%;
      height: 100px;
  }
      
  .arrow_up{
      width: 10%;
      float: left;
  }
       
  .select_order{
      width: 90%;
      height: 100%;
        float: left;
  }
  
  .firstchild {
              top: 0;
              left: 0;
  }
      
  .childClass {
              position: absolute;
              color: #ffffff;
  }
  
  /* Responsive layout - when the screen is less than 800px wide, make the two columns stack on top of each other instead of next to each other */
  @media screen and (max-width: 800px) {
  
      .leftcolumn, .rightcolumn {   
      width: 100%;
      padding: 0;
      }
  
.card {
  background-color: transparent;
}

    .img2 {
      width:0px;
    padding: 0px;
    border-spacing: 0px;
    }
  
     .badge2{
      width: 100%;
      height: 100%;
        float: right;
        background: #03080f;
        border-spacing: 0px;
        padding:10px;
    }
  
    .circle {
      float: right;
    }

      .text2 {
         width: 100%;
         background-color: transparent;
      }
  
      .content{
         background-color: #0e1a2b;
      }

      .circle {
         margin-top:5px;
      }
  
  }
  
  </style>

