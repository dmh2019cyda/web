<template>
  <v-layout>
    <v-flex text-xs-center>

        <v-list two-line>
          <template v-for="(item, index) in items">
            <v-subheader
              v-if="item.header"
              :key="item.header"
            >
              {{ item.header }}
            </v-subheader>

            <v-divider
              v-else-if="item.divider"
              :inset="item.inset"
              :key="index"
            ></v-divider>

            <v-list-tile
              v-else
              :key="item.title"
              avatar
            >
              <v-list-tile-avatar>
                <img :src="item.avatar">
              </v-list-tile-avatar>

              <v-list-tile-content>
                <v-list-tile-title v-html="item.title"></v-list-tile-title>
                <v-list-tile-sub-title v-html="item.subtitle"></v-list-tile-sub-title>
              </v-list-tile-content>
            </v-list-tile>
          </template>
        </v-list>

    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    data () {
      return {
        items: [
          { header: 'Today' },
          {
            avatar: 'https://cdn.vuetifyjs.com/images/lists/1.jpg',
            title: '成人晚間舞蹈班',
            subtitle: "路德會友安長者中心 - 星期一至星期六：上午九時正至下午五時正"
          },
          { divider: true, inset: true },
          {
            avatar: 'https://cdn.vuetifyjs.com/images/lists/2.jpg',
            title: '成人晚間瑜珈班',
            subtitle: "葵青社區會堂社區中心 - 星期一至星期六：上午九時正至下午五時正"
          },
          { divider: true, inset: true },
          {
            avatar: 'https://cdn.vuetifyjs.com/images/lists/3.jpg',
            title: '成人晚間體藝班',
            subtitle: "葵青社區會堂社區中心 - 星期一至星期六：上午九時正至下午五時正"
          },
          { divider: true, inset: true },
          {
            avatar: 'https://cdn.vuetifyjs.com/images/lists/4.jpg',
            title: '成人晚間才藝班',
            subtitle: "西貢區社區中心 - 星期一至星期六：上午九時正至下午五時正"
          },
          { divider: true, inset: true },
          {
            avatar: 'https://cdn.vuetifyjs.com/images/lists/5.jpg',
            title: '長者學苑',
            subtitle: "路德會友安長者中心 - 星期一至星期六：上午九時正至下午五時正"
          }
        ]
      }
    }
  }
</script>
