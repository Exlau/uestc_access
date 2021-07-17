<template>
  <div class="home">
    <info-form v-if="showForm" @submitInfo="updateInfo"></info-form>
    <div class="main">
      <div class="accessInfo">{{ info.text }}</div>
      <div class="personInfo">
        <div class="name info_item">
          <img class="svg" src="../assets/user.svg" />
          <div class="info_label">用户姓名</div>
          <div class="info_text">{{ info.name }}</div>
        </div>
        <div class="kind info_item">
          <img class="svg" src="../assets/login.svg" />
          <div class="info_label">登记类型</div>
          <div class="info_text">{{ info.kind }}</div>
        </div>
        <div class="time info_item">
          <img class="svg" src="../assets/time.svg" />
          <div class="info_label">登记时间</div>
          <div class="slidePart">
            <span class="timeRoll">{{ info.time }} </span>
            <span class="timeRoll">{{ info.time }} </span>
            <span class="timeRoll">{{ info.time }} </span>
          </div>
        </div>
        <el-button class="scanBtn">前往个人二维码</el-button>
        <div class="logo">
          <img class="logo_img" src="../assets/uestc.png" alt="logo" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import InfoForm from "@/components/InfoForm.vue";

export default {
  name: "Home",
  components: {
    InfoForm,
  },
  data() {
    return {
      showForm: true,
      info: {
        text: "本科用户，入校授权有效！",
        name: "",
        kind: "本科生",
        time: "",
      },
    };
  },
  beforeCreate() {
    this.showForm = true;
  },
  methods: {
    updateInfo(data) {
      this.info.name = data.user;
      this.showForm = false;

      const timeNow = new Date();
      let year = timeNow.getFullYear();
      let month = timeNow.getMonth() + 1;
      let date = timeNow.getDate();
      let hour = timeNow.getHours();
      let min = timeNow.getMinutes();
      let sec = timeNow.getSeconds();
      if (month < 10) month = "0" + month;
      if (date < 10) date = "0" + date;
      this.info.time =
        year + "-" + month + "-" + date + " " + hour + ":" + min + ":" + sec;
    },
  },
};
</script>
<style >
.home {
  background: #fff;
}

.accessInfo {
  color: #377e21;
  font-weight: 600;
  font-size: 1.4rem;
  padding: 2.5rem 1rem;
  border-bottom: 1.5px solid #eee;
}
.personInfo {
  padding: 1.1rem;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}

.info_label {
  color: #212121;
  font-weight: 500;
  font-size: 1rem;
  flex: 1;
}

.info_item {
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.info_text {
  font-size: 1.4rem;
  font-weight: 600;
  letter-spacing: 1px;
}
.slidePart {
  position: relative;
  flex: 1;
  overflow: hidden;
}

.timeRoll {
  position: relative;
  left: 0;
  font-family: sans-serif;
  font-weight: 600;
  color: #58c1a5;
  /* flex: 1; */
  overflow: hidden;
  white-space: nowrap;
  animation: slide 10s linear infinite;
}

@keyframes slide {
  0% {
    left: 0;
  }
  100% {
    left: -200%;
  }
}

@keyframes scrols {
  from {
    transform: translateX(100%);
  }
  to {
    transform: translateX(-100%);
  }
}

.scanBtn {
  text-align: center !important;
  transform: translateX(-50%);
  margin: 0 50% !important;
  background-color: #58c1a5 !important;
  color: white !important;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.12), 0 0 6px rgba(0, 0, 0, 0.04);
}

.svg {
  width: 22px;
  height: 22px;
  margin-right: 0.5rem;
}

.logo {
  width: 3.5rem;
  margin-top: 2rem;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 0;
}

.logo_img {
  width: 100%;
}
</style>
