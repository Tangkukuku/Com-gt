<template>
    <div>
        <main-header navsel="front"></main-header>
        <br><br><br>
        <center><h1>Edit User</h1>
        <form v-on:submit.prevent = "editUser">
            <table border="0">
            <tr>
                <th class="d">
                    <center><b>name:</b></center>
                </th>
                <th class ="c">
                    <input class="form-control center_div" type="text" v-model="user.name">
                </th>
            </tr>
            <br>
            <tr>
                <th class="d">
                    <center><b>lastname:</b></center>
                </th>
                <th class ="c">
                    <input class="form-control center_div" type="text" v-model="user.lastname">
                </th>
            </tr>
            <br>
            <tr>
                <th class="d">
                    <center><b>email:</b></center>
                </th>
                <th class ="c">
                    <input class="form-control center_div" type="text" v-model="user.email">
                </th>
            </tr>
            <br>
            <tr>
                <th class="d">
                    <center><b>address:</b></center>
                </th>
                <th class ="c">
                    <input class="form-control center_div" type="text" v-model="user.address">
                </th>
            </tr>
            
            </table>
            <br>
                <p>
                    <button class="btn btn-success btn-sm" type="submit">edit user</button>
                    <button class="btn btn-sm secondary" v-on:click="navigateTo('/front-cartlist')">Back..</button>
                </p>
            
        </form>
        
            
        
    </center>
    
    </div>
</template>
<script>
    import UsersService from '@/services/UsersService'
    export default {
        data () {
            return {
                user: {
                    name: '',
                    lastname: '',
                    email: '',
                    password: '',
                    status: 'active'
                }
            }
        },
        methods: {
            async editUser () {
                try {
                    await UsersService.put(this.user)
                    this.$router.push({
                    name: 'cartlist-userId'
                })
                } catch (err) {
                    console.log(err)
                }
            },
            navigateTo (route) {
                this.$router.push(route)
            },
        },
        async created () {
            try {
                let userId = this.$route.params.userId
                this.user = (await UsersService.show(userId)).data
            } catch (error) {
                console.log (error)
            }
        }
    }
</script>
<style scoped>
    .center_div {
        width:100%;
    }
    .c {
        width: 600px ;
    }
    .d{
        width: 100px ;
    }
       .site-footer
{
  background-color:#26272b;
  padding:45px 0 20px;
  font-size:16px;
  line-height:24px;
  color:#737373;
}
.site-footer hr
{
  border-top-color:#bbb;
  opacity:0.5
}
.site-footer hr.small
{
  margin:20px 0
}
.site-footer h6
{
  color:#fff;
  font-size:20px;
  text-transform:uppercase;
  margin-top:5px;
  letter-spacing:2px
}
.site-footer a
{
  color:#737373;
}
.site-footer a:hover
{
  color:#3366cc;
  text-decoration:none;
}
.footer-links
{
  padding-left:0;
  list-style:none
}
.footer-links li
{
  display:block
}
.footer-links a
{
  color:#737373
}
.footer-links a:active,.footer-links a:focus,.footer-links a:hover
{
  color:#3366cc;
  text-decoration:none;
}
.footer-links.inline li
{
  display:inline-block
}
.site-footer .social-icons
{
  text-align:right
}
.site-footer .social-icons a
{
  width:40px;
  height:40px;
  line-height:40px;
  margin-left:6px;
  margin-right:0;
  border-radius:100%;
  background-color:#33353d
}
.copyright-text
{
  margin:0
}
@media (max-width:991px)
{
  .site-footer [class^=col-]
  {
    margin-bottom:30px
  }
}
@media (max-width:767px)
{
  .site-footer
  {
    padding-bottom:0
  }
  .site-footer .copyright-text,.site-footer .social-icons
  {
    text-align:center
  }
}
.social-icons
{
  padding-left:0;
  margin-bottom:0;
  list-style:none
}
.social-icons li
{
  display:inline-block;
  margin-bottom:4px
}
.social-icons li.title
{
  margin-right:15px;
  text-transform:uppercase;
  color:#96a2b2;
  font-weight:700;
  font-size:13px
}
.social-icons a{
  background-color:#eceeef;
  color:#818a91;
  font-size:16px;
  display:inline-block;
  line-height:44px;
  width:44px;
  height:44px;
  text-align:center;
  margin-right:8px;
  border-radius:100%;
  -webkit-transition:all .2s linear;
  -o-transition:all .2s linear;
  transition:all .2s linear
}
.social-icons a:active,.social-icons a:focus,.social-icons a:hover
{
  color:#fff;
  background-color:#29aafe
}
.social-icons.size-sm a
{
  line-height:34px;
  height:34px;
  width:34px;
  font-size:14px
}
.social-icons a.facebook:hover
{
  background-color:#3b5998
}
.social-icons a.twitter:hover
{
  background-color:#00aced
}
.social-icons a.linkedin:hover
{
  background-color:#007bb6
}
.social-icons a.dribbble:hover
{
  background-color:#ea4c89
}
@media (max-width:767px)
{
  .social-icons li.title
  {
    display:block;
    margin-right:0;
    font-weight:600
  }
}
</style>