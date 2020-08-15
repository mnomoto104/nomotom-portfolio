<template>
  <v-container fluid class="my-6 mx-0 px-0">
    <v-layout align-center>
      <v-flex>
        <section class="my-2">
          <div class="text-title">Self-Introduction</div>
          <v-divider></v-divider>

          <v-row class="mt-12" justify="center">
            <v-avatar size="210px">
              <img alt="Avatar" src="avatar2.jpg" />
            </v-avatar>
          </v-row>
          <v-row justify="center">
            <div class="my-4 text-subtitle-2">
              <p class="text-center">
                Masanori Nomoto
                <br />Birthday: 1983/05/20
                <br />16Personalities: ENTJ
              </p>
              <p class="text-center">
                大手通信会社やコンサルティング会社にて、
                <br />エンジニア、コンサルタント、情報セキュリティ、マネージャー、教育など
                <br />企業におけるIT活動全般を経験してきました。
                <br />コンセプチュアルなものを形にすること、作ること、人を育てることに適性があります。
                <br />思考と仕事が趣味で、海が好き。愛妻家。
                <br />モットーは、"楽しむしかない"
              </p>
            </div>
          </v-row>
        </section>

        <section class="my-12">
          <div class="text-title">Works</div>
          <v-divider></v-divider>
          <v-row class="mt-6">
            <v-col cols="12" sm="6" md="4" v-for="(item, i) in cardItems" :key="i">
              <v-hover v-slot:default="{ hover }">
                <v-card
                  :elevation="hover ? 6 : 2"
                  :class="{ 'on-hover': hover }"
                  class="mx-auto"
                  height="auto"
                >
                  <v-img class="white--text align-end" height="200px" :src="cardItems[i].img">
                    <v-card-title class="py-1 cardColor text-subtitle-1">{{ cardItems[i].title }}</v-card-title>
                  </v-img>
                  <v-card-text class="py-4 pb-1 text--primary">
                    <div>{{ cardItems[i].text }}</div>
                  </v-card-text>
                  <v-card-actions class="pt-0 pb-2">
                    <v-btn color="blue darken-3" text>Details</v-btn>
                  </v-card-actions>
                  <v-divider></v-divider>
                  <v-card-actions>
                    <v-chip
                      class="my-1 mr-1"
                      small
                      color="primary"
                      v-if="cardItems[i].tag[0]"
                    >{{ cardItems[i].tag[0] }}</v-chip>
                    <v-chip
                      class="my-1 mr-1"
                      small
                      color="primary"
                      v-if="cardItems[i].tag[1]"
                    >{{ cardItems[i].tag[1] }}</v-chip>
                    <v-chip
                      class="my-1 mr-1"
                      small
                      color="primary"
                      v-if="cardItems[i].tag[2]"
                    >{{ cardItems[i].tag[2] }}</v-chip>
                    <v-chip
                      class="my-1 mr-1"
                      small
                      color="primary"
                      v-if="cardItems[i].tag[3]"
                    >{{ cardItems[i].tag[3] }}</v-chip>
                    <v-chip
                      class="my-1 mr-1"
                      small
                      color="primary"
                      v-if="cardItems[i].tag[4]"
                    >{{ cardItems[i].tag[4] }}</v-chip>
                    <v-chip
                      class="my-1 mr-1"
                      small
                      color="primary"
                      v-if="cardItems[i].tag[5]"
                    >{{ cardItems[i].tag[5] }}</v-chip>
                  </v-card-actions>
                </v-card>
              </v-hover>
            </v-col>
          </v-row>
        </section>

        <section class="my-12">
          <div class="text-title">Skills</div>
          <v-divider></v-divider>
          <v-row class="mt-8" justify="center">
            <v-card elevation="0">
              <v-data-table
                :headers="headers"
                :items="desserts"
                :items-per-page="8"
                hide-default-footer
                class="elevation-1"
              >
                <template v-slot:item.calories="{ item }">
                  <v-chip :color="getColor(item.calories)" dark>{{ item.calories }}</v-chip>
                </template>
              </v-data-table>
            </v-card>
          </v-row>
        </section>

        <section class="my-12">
          <div class="text-title">Cotact</div>
          <v-divider></v-divider>
          <v-row class="mt-2" justify="center"></v-row>
        </section>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    cardItems: [
      {
        title: "Internal System Development",
        text:
          "社内システム開発におけるプロジェクトマネジメント、要件定義、技術選定、デザイン、モックアップ、基本設計、詳細設計、フロントエンド開発、マークアップまで担当。",
        img: "b.jpg",
        tag: ["HTML/CSS", "Nuxt.js", "AWS", "Chart.js"],
      },
      {
        title: "Data Analysis",
        text:
          "人事データ等を基にクラスター分析、回帰分析、主成分分析などを行い、150ページ(ppt)程度の企業分析レポート作成、及び、個人分析レポートの作成(ツール開発含む)。",
        img: "c.jpg",
        tag: ["Python", "Pandas", "matplotlib"],
      },
      {
        title: "Tool Development",
        text:
          "インターナルな業務支援ツール、業務自動化ツール、Webスクレイピングツール、Webマーケティングツール、形態素解析ツール、などのデスクトップアプリ/ツールの開発運用。",
        img: "d.jpg",
        tag: ["HTML/CSS", "Nuxt.js", "Python", "VBA"],
      },
      {
        title: "New Build of ISO27001",
        text:
          "ISO27001認定のため推進責任者としてISMSを新規構築。プロジェクトマネジメント、ISOドキュメント作成、リスク分析、ISOコンサルなしで審査/運用まで実施。",
        img: "e.jpg",
        tag: ["Management", "ISO7001"],
      },
      {
        title: "Consalting",
        text:
          "クライアントへのヒアリング、提案、設計、プロジェクトへの参画、ステークホルダーとの相対/調整、ネゴシエーション、トータルで40社以上の実績があります。",
        img: "f.jpg",
        tag: ["Consulting", "Proposal"],
      },
      {
        title: "IT Management",
        text:
          "IT事業部のマネージャーとして、業務プロセス改善や標準化、最適化、DXを推進、事業再設計などの企画や計画の策定/推進。ジュニアメンバーへの育成指導メンタルケア。",
        img: "h.jpg",
        tag: ["Management", "Planning", "Team Building"],
      },
    ],
    headers: [
      {
        text: "Skill",
        align: "start",
        sortable: false,
        value: "name",
      },
      { text: "Years of Experience", value: "calories" },
    ],
    desserts: [
      {
        name: "HTML/CSS",
        calories: 5,
      },
      {
        name: "js",
        calories: 5,
      },
      {
        name: "Python",
        calories: 3,
      },
      {
        name: "Nuxt.js",
        calories: 3,
      },
      {
        name: "VB.net",
        calories: 8,
      },
      {
        name: "AWS",
        calories: 2,
      },
      {
        name: "Linux",
        calories: 4,
      },
      {
        name: "Oracle",
        calories: 4,
      },
    ],
  }),
  methods: {
    getColor(calories) {
      if (calories > 400) return "red";
      else if (calories > 200) return "orange";
      else return "green";
    },
  },
};
</script>

<style>
.cardColor {
  background-color: rgba(46, 40, 40, 0.418) !important;
  border-color: white !important;
}
.v-card {
  transition: opacity 0.5 ease-in-out;
}
.v-card:not(.on-hover) {
  opacity: 0.7;
}
</style>