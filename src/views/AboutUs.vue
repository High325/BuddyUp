<template>
  <div class="page" style="text-align: center" v-if="user">
    <TopBar :componentName="componentName"/>
    <SideBar />
    <div class="info">
      <img
        id="aboutUsLogo"
        src="@/assets/aboutus.png"
        width="150"
        alt="About Us" />
      <br />
      <h2>About Us</h2>
      <p>
        Buddy Up serves as an all-in-one platform solely for volunteers’ use. The
        app aims to match volunteers with elderlies who are socially isolated and/
        or have chronic diseases. Buddy Up will request the elderlies’ preferences
        data from the organisations and partner organisations will not have to
        interact with our web application’s interface. Users that registered
        themselves as volunteers will then be matched with elderlies according to
        their preferences, and they can then visit their buddies at their
        respective homes. Volunteers are mainly expected to provide preventive
        care for their buddies and keep them company. Once matched, the platform
        will prompt users to record their visitation details in a form and set
        reminders for themselves while caring for the elderlies, enabling them to
        render the most support possible with the least amount of stress.
      </p>
      <br />
      <h2>Some Background on the Issue</h2>
      <p>
        Singapore has one of the lowest fertility rates in the world at 1.15
        children per woman while having one of the highest life expectancies. This
        has resulted in an ageing population, with 23.1 elderly per 100
        non-elderly Singaporean residents, which puts pressure on Singapore’s
        shrinking workforce. Furthermore, social isolation for elderlies has also
        become an issue. 67,600 elderly (65 years and above) live alone as of
        2019, making up 11.6% of the elderly population in Singapore. This number
        is expected to increase to 83,000 by 2030. This social isolation issue has
        prompted the setting up of programmes such as Neighbours for Active Living
        to ensure that patients with complex health and social care needs continue
        to receive care in the community after discharge. However, such programmes
        rely on volunteers, and volunteerism rates have decreased by 7% in 2021,
        partly due to the COVID-19 pandemic.
      </p>
      <br />
      <h2>How does Buddy Up help resolve this issue?</h2>
      <p>
        Despite volunteers being in high demand, there are still significant
        barriers to entry for individuals who are looking to begin volunteering.
        For instance, the experience could be stressful due to potential language
        barriers or large time commitments. Furthermore, prospective volunteers
        are faced with issues on how to begin the volunteering process. In the
        context of caring for elderlies, the quality of care provided may be
        compromised if there are too many elderlies paired with a single
        volunteer.
      </p>

      <p>
        Buddy Up will increase the quality of care for the elderly by providing
        volunteers with the necessary tools, while also improving the experience
        for volunteers. Through streamlining the volunteering process, it makes
        volunteering more accessible through a comprehensive platform. By
        increasing charity organisation reach for volunteers and capping the
        number of beneficiaries per volunteer, our application would result in
        higher volunteerism adoption and retention rates and thereby improve
        social and health outcomes for the elderly.
      </p>
    </div>
  </div>
  <div v-else>
    <h1>You must be logged in to view this page</h1>
    <Login route="aboutus" />
  </div>
</template>

<script>
import TopBar from "../components/TopBar.vue";
import SideBar from "../components/SideBar.vue";
import Login from "../components/Login.vue";
import { getAuth, onAuthStateChanged } from "firebase/auth";

export default {
  components: {
    TopBar,
    SideBar,
    Login,
  },

  data() {
    return {
      user: true,
      componentName:"About Us"
    };
  },

  mounted() {
    const auth = getAuth();
    onAuthStateChanged(auth, (user) => {
      if (user) {
        this.user = user;
      } else {
        this.user = false;
      }
    });
  },
};
</script>

<style>
p {
  text-align: justify;
  margin-left: 5%;
  margin-right: 5%;
}

.page {
  margin-left: 120px;
  background-color: #fff8f8
}

#aboutUsLogo {
  float: right;
  height: 300px;
  width: auto;
  margin: 20px;
}

.info {
  background: #ffffff;
  margin-top: 30px;
  margin-bottom: 150px;
  margin-right: 40px;
  margin-left: 120px;
  border: 3px solid #f07575;
  border-radius: 20px;
}

h2 {
  font-size: 30px;
  font-weight: bold;
  color: #411d1d;
}
</style>