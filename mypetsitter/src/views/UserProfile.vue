<template>
  <div class="user-profile">
    <div class="user-profile__sidebar">
      <div class="user-profile__user-panel">
        <h1 class="user-profile__user-name">{{ user.username }}</h1>
        <div class="user-profile__admin-badge" v-if="user.isAdmin">Admin</div>
        <div class="user-profile__follower-count">
          <strong>Followers: </strong> {{ followers }}
        </div>
      </div>
      <CreateTwootPanel @add-twoot="addTwoot"/>
    </div>

    <div class="user-profile__toots-wrapper">
      <TwootItem
          v-for="twoot in user.twoots"
          :key="twoot.id"
          :username="user.username"
          :twoot="twoot"/>
    </div>
  </div>

</template>

<script>
import TwootItem from "../components/TwootItem";
import CreateTwootPanel from "../components/CreateTwootPanel";

export default {
  name: 'UserProfile',
  components: {
    TwootItem,
    CreateTwootPanel
  },
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: 'khushbu',
        firstName: 'khushbu',
        lastName: 'Singh',
        email: 'khushbuv84@gmail.com',
        isAdmin: true,
        twoots: [
          {id: 1, content: 'Towtter is amazing'},
          {id: 2, content: "Don't forget to subscribe"}
        ],
      },
    }
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount)
        console.log(this.user.username + " has gained a follower!");
    },
    test(newTestCount, oldTestCount) {
      if (newTestCount > oldTestCount)
        console.log("new test value: " + this.test)
    }
  },
  methods: {
    followUser() {
      this.followers++;
    },
    userNameChange() {
      this.user.username = "Amit";
    },
    addTwoot(twoot) {
      this.user.twoots.unshift({
        id: this.user.twoots.length + 1,
        content: twoot
      })
      this.newTwootContent = ''
    }
  },

  mounted() {
    this.followUser();
  }
}
</script>

<style lang="scss" scoped>
.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  //width: 100%;
  grid-gap: 50px;
  padding: 50px 5%;

  .user-profile__user-panel {
    display: flex;
    flex-direction: column;
    //margin-right: 50px;
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border: 1px solid #DFE3E8;
    margin-bottom: auto;

    .user-profile__user-name {
      text-align: left;
    }

    h1 {
      margin: 0;
    }

    .user-profile__admin-badge {
      background: rebeccapurple;
      color: white;
      border-radius: 5px;
      margin-right: auto;
      padding: 0px 10px;
      font-weight: bold;
    }
  }

  .user-profile__toots-wrapper {
    display: grid;
    grid-gap: 10px;
    margin-bottom: auto;
  }
}


</style>
