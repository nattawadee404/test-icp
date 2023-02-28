<template>
  <nav>
    <q-layout view="lHh Lpr lFf">
      <q-toobar-side-icon class="grey--text" @click="drawer = !drawer">
      </q-toobar-side-icon>
      <!-- <q-toolbar-title class="grey--text">
        รหัส :
        <label for="member_id">{{ $store.getters.myMember_id }}</label>
        /
        <label for="myName">{{ $store.getters.myName }}</label>
      </q-toolbar-title> -->
      <q-spacer></q-spacer>
      <!-- <q-btn
        flat
        color="grey"
        v-if="!$store.getters.myAuthenticate"
        icon="login"
        @click="onLogin"
        ><q-tooltip :target="true"> เข้าสู่ระบบ </q-tooltip>>
      </q-btn>
      <q-btn
        v-if="$store.getters.myAuthenticate"
        flat
        color="grey"
        icon="logout"
        @click="onLogout"
      >
        <q-tooltip :target="true"> ออกจากระบบ </q-tooltip>
      </q-btn> -->
      <q-navigation-drawer app v-model="drawer" class="indigo">
        <q-list>
          <EssentialLink
            v-for="link in essentialLinks"
            :key="link.title"
            v-bind="link"
          />
        </q-list>
      </q-navigation-drawer>
      <q-page-container>
        <router-view />
      </q-page-container>
    </q-layout>
  </nav>
</template>

<script>
import { defineComponent, ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";
const linksList = [
  {
    title: "กำหนดข้อมูลส่วนตัว",
    caption: "การศึกษา ความพิการ",
    icon: "lock_outline",
    link: "/FormComponent",
  },
  {
    title: "กำหนดอาชีพเป้าหมาย",
    caption: "อาชีพในอนาคต",
    icon: "work_history",
    link: "/FormPlanCareer",
  },
  {
    title: "กำหนดคุณสมบัติ/ทักษะ",
    caption: "คุณสมบัติและทักษะ เป้าหมาย ระดับ",
    icon: "fact_check",
    link: "/FormQualification",
  },
  {
    title: "การพัฒนาตนเอง",
    caption: "ศึกษาเรียนรู้ ฝึกปฏิบัติ",
    icon: "post_add",
    link: "/FormPlan",
  },
  {
    title: "การประเมินตนเอง",
    caption: "เดือน ระดับ",
    icon: "checklist_rtl",
    link: "/FormSelfAssessment",
  },
  {
    title: "รายงานแผนการพัฒนาตนเอง",
    caption: "ผลการพัฒนาตนเอง",
    icon: "summarize",
    link: "/FormReport",
  },
  {
    title: "รายงานการประเมินตนเอง",
    caption: "ผลการประเมินตนเอง",
    icon: "summarize",
    link: "/FormPivotTable",
  },
];
export default {
  name: "IcpHome",
  data() {
    return {
      drawer: false,
    };
  },
  components: {
    EssentialLink,
  },
  methods: {
    onLogin() {
      this.$router.replace({ name: "LoginPage1" });
    },
    onLogout() {
      this.$router.replace({ name: "LogoutPage" });
    },
    // toggleLeftDrawer() {
    //   this.onclick = !this.onclick;

    //   leftDrawerOpen.value = !leftDrawerOpen.value;
    // },
  },
};
</script>

<style></style>
