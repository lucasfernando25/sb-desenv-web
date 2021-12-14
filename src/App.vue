<template>
  <v-app id="inspire">
    <v-app-bar app flat dark class="ma-3" clipped-right>
      <v-container class="py-0 fill-height">
        <v-icon v-for="(link, index) in icones" :key="index" text class="mr-6" v-bind:class="{'orange--text': index === 4}">
          {{ link }}
        </v-icon>

        <v-spacer></v-spacer>
        <div class="right">
          <img src="https://static.todamateria.com.br/upload/ba/nd/bandeira_americana_bb.jpg" color="grey darken-1" size="32" style="height: 1rem" alt="">
          <p color="grey darken-1" size="32">English</p>
          <v-icon>mdi-white-balance-sunny</v-icon>
          <v-icon>mdi-magnify</v-icon>
          <v-badge color="purple" content="5">
            <v-icon>mdi-cart-outline</v-icon>
          </v-badge>
          <v-badge color="red" content="6">
            <v-icon>mdi-bell-outline</v-icon>
          </v-badge>
          <div class="name">
            <p class="name--title text-h6">John snow</p>
            <small>King of the North</small>
          </div>
          <v-list-item-avatar>
            <v-img src="https://randomuser.me/api/portraits/men/85.jpg"></v-img>
          </v-list-item-avatar>
        </div>
      </v-container>
    </v-app-bar>

    <div class="left-navigation">
      <v-navigation-drawer v-model="drawer" app dark>
        <v-sheet class="pa-4">
          <div class="text-h5 pb-3 deep-purple--text">ASSSSS</div>
          <v-badge color="orange" content="2">
            <v-icon class="pr-3">mdi-home</v-icon>
            <span>Dashboards</span>
          </v-badge>
        </v-sheet>

        <v-sheet class="pl-4 pt-4"> APPS & PAGES</v-sheet>
        <v-list>
          <v-list-item
              v-for="([icon, text], index) in links"
              :key="index"
              link
              v-bind:class="{ selected: index === 7 }"
          >
            <v-list-item-icon>
              <v-icon>{{ icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>{{ text }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
    </div>
    <v-main>
      <div class="right-navigation">
        <v-navigation-drawer
            class="v-main"
            style="margin-top: 10rem;"
            dark
            app
            right
        >
          <v-col>
            <v-text-field placeholder="Search here" outlined></v-text-field>
          </v-col>
          <v-sheet class="pl-4 pt-4"> RECENT POSTS</v-sheet>
          <v-container>
            <v-row>
              <template v-for="(recent, i) in recents">
                <v-col :key="recent" class="mt-2" cols="12" style="display: flex">
                  <v-img
                      width="120"
                      :src="`https://source.unsplash.com/random/370x250?${i}`"
                  ></v-img>
                  <v-container>
                    <strong class="white--text">{{ recent.title }}</strong>
                    <p class="white--text">{{ recent.date }}</p>
                  </v-container>
                </v-col>
              </template>
            </v-row>
          </v-container>
        </v-navigation-drawer>
      </div>

      <div class="pa-4 white--text d-flex navigator" style="background-color: transparent" dark>
        <div class="text-h5">Blog List</div>
        <div class="text-h5">|</div>
        <v-icon>mdi-home-outline</v-icon>
        <div>></div>
        <div class="purple-text">Pages</div>
        <div>></div>
        <div class="purple-text">Blog</div>
        <div>></div>
        <div>List</div>
      </div>
      <v-row>
        <v-col class="py-8 px-6" v-for="(card, i) in cards" :key="card">
          <template>
            <v-card max-width="300" dark>
              <template slot="progress">
                <v-progress-linear
                    color="deep-purple"
                    height="10"
                    indeterminate
                ></v-progress-linear>
              </template>

              <v-img
                  height="175"
                  :src="`https://source.unsplash.com/random/500x500?${i}`"
              ></v-img>

              <v-card-title>{{ card.title }}</v-card-title>

              <div class="person d-flex" style="width: 100%; justify-content: space-evenly; align-items: center">
                <img src="https://randomuser.me/api/portraits/men/85.jpg" style="height: 2rem; width: 2rem;background-size: cover ; border-radius: 50px">
                <p style="color: gray">by</p>
                <p>Someone</p>
                <p style="color: gray">|</p>
                <p style="color: gray">Jan 10, 2020</p>
              </div>

              <v-card-text>
                <v-chip-group
                    v-model="selection"
                    active-class="deep-purple accent-4 white--text"
                    column
                    v-for="tag in card.tags"
                    :key="tag"
                >
                  <v-chip>{{ tag }}</v-chip>
                </v-chip-group>
              </v-card-text>

              <v-card-text>
                <div>
                  {{ card.descript }}
                </div>
              </v-card-text>
            </v-card>
          </template>
        </v-col>
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    drawer: null,
    links: [
      ["mdi-email", "Email"],
      ["mdi-message", "Chat"],
      ["mdi-format-list-checks", "Todo"],
      ["mdi-calendar", "Calendar"],
      ["mdi-file-multiple", "Invoice"],
      ["mdi-cart-outline", "eCommerce"],
      ["mdi-account", "User"],
      ["mdi-file-star-outline", "Pages"],
    ],
    tags: [{name: "Quote", color: "#4e96ac", backgroundcolor: "#4e96ac"}],
    icones: [
      "mdi-calendar",
      "mdi-message",
      "mdi-email",
      "mdi-format-list-checks",
      "mdi-star-outline",
    ],

    cards: [
      {
        title: "The Best Features Coming to iOS and Web design",
        author: "Chani Pradita",
        tags: ["Quote", "Fashion"],
        descript:
            "Donut fruitcake soufflé apple pie candy canes jujubes croissant...",
        imageUrl:
            "https://images.pexels.com/photos/7932264/pexels-photo-7932264.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940",
      },
      {
        title: "Latest Quirky Opening Sentence or Paragraph",
        author: "Jorge Griffin",
        tags: ["Gaming", "Video"],
        descript:
            "Apple pie caramels lemon drops halvah liquorice carrot cake...",
        imageUrl:
            "https://images.pexels.com/photos/8960464/pexels-photo-8960464.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940",
      },
    ],
    recents: [
      {
        title: "Why Should Forget Facebook",
        date: "Jan 14 2020",
      },
      {
        title: "Publish your passion, your way",
        date: "Mar 04 2020",
      },
      {
        title: "The Best Ways to Retain More",
        date: "Feb 18 2020",
      },
      {
        title: "Share a Shocking Fact or Statistc",
        date: "Sep 08 2020",
      },
    ],
  }),
};
</script>

<style lang="scss">
.v-main {
  background-color: #161d30;
}

.left-navigation {
  .v-navigation-drawer__content,
  .theme--dark.v-sheet {
    background-color: #292f45 !important;
  }
}

.right-navigation {
  .v-navigation-drawer{
    width: 20rem !important;
  }
  .v-navigation-drawer__content{
    background-color: #161d30 !important;
    width: 20rem;
  }
}

.theme--dark.v-sheet {
  background-color: #292f45 !important;
}

.v-card__text {
  display: flex;
}

.selected {
  .theme--dark.v-icon {
    color: gray !important;
  }

  background-color: white !important;
  color: gray !important;
}

.name {
  display: flex;
  flex-direction: column;

  > p {
    margin: 0 !important;
  }

  &--title {
    align-self: flex-end;
    font-weight: 600;
  }
}

.right {
  display: flex;
  align-items: center;
  justify-content: space-around;
  width: 28rem;

  > p {
    margin: 0 !important;
  }
}

.selected {
  .theme--dark.v-icon {
    color: gray !important;
  }

  background-color: white !important;
  color: gray !important;
}

.navigator {
  align-content: center;
  text-align: center;

  .theme--light.v-icon, .purple-text {
    color: mediumpurple;
  }

  > div {
    display: flex;
    text-align: center;
    align-self: center;
    padding: 0 0.5rem;
  }
}

.person{
  >p{
    margin: 0 !important;
  }
}


</style>
