<template>
  <div>
    <h1>Conference Sessions Information</h1><br>
    <!-- Buttons using @click -->
    <button @click="showAllSessions">Sessions</button>
    <button @click="showMySessions">My Sessions</button><br>
    <br>
    <div class="holder">
      <!-- v-for --> <!-- v-for -->
      <div class="session" v-for="session in sessions" :key="session.id">
        <h3> {{ session.title }} </h3>
        <h4 class="bigInfo"> Presented by: <span id="person">{{ session.presenter }}</span>, {{ session.sDay }} at {{ session.sTime }}:00 P.M.</h4>
        <p class="desc"> {{ session.desc }}</p>
        <!-- Button -->
        <p> Tags: <span>{{ session.tags[0] }}</span> <span>{{ session.tags[1] }}</span> <span>{{ session.tags[2] }}</span> <button @click="joinConference">Join</button></p>
      </div>
    </div>
    <div class="myConferences">
      <!-- <h1>TEST</h1> -->
    <!-- This is where conferences go when you click its button-->
    <!-- v-for -->
    <div v-for="joinedSession in joined" :key="joinedSession.id">
        <h3> {{ joinedSession.title }} </h3>
        </div>
</div>
  </div>
</template>

<style scoped>
* {
  color: white;
}
button {
  background-color: gray;
  margin: 10px;
  border-radius: 5px;
}

.session{
  background-color: #36454F;
  border-radius: 5px;
  padding: 5px;
  width: 100%;
  margin: 10px;
}

span{
  background-color: #04d9ff;
  color: black;
  border-radius: 5px;
  padding: 1px;
  margin: 1px;
  border: none;
}

.desc{
  font-size: smaller;
}

.bigInfo{
  border-bottom: black solid 2px;
}

#person{
  background-color: #39FF14;
}
.myConferences {
  display: none;
}
</style>

<script lang="ts">
export default {
  data() {
    return {
      sessions: [
      /* This is the array (edited slightly to make it not so big in the editor, but still big), put the script at the end because of it*/
        {
          id: 1,
          title: "Beyond Request/Response: Why and how we should change the way we build web applications",
          desc: "As web developers, we have been building web applications the same way for 25 years. We send a request, and we receive a response. We might get a whole page back, or we might get some data to render, but the common thread for almost every web application that has ever been built is the request/response cycle. What if we did not have to do it this way? What kind possibilities would open up to us?",
          presenter: "Chris Nelson",
          tags: ["Javascript", "Front End", "Programming"],
          sTime: 8,
          sDay: "Thursday",
          added: false
        },
        {
          id: 2,
          title: "Build a Modern Single Page Application with Vue",
          desc: "You will learn the latest tools and patterns Vue offers for building reusable and testable UI code. You will get hands-on practice scaling an app to multiple pages using routing and state management libraries. At the end of this workshop, you will be ready to build complex and responsive front-end applications.",
          presenter: "Matt Burke",
          tags: ["Javascript", "Front End"],
          sTime: 13,
          sDay: "Friday",
          added: false
        },
        {
          id: 3,
          title: "Building a Web Component Library",
          desc: "Web components have been around for a long time (since HTML 5 became a thing), but there has not been a lot of attention given to them until recently. Now, tech organizations worldwide are adopting them and finding tremendous efficiency in creating framework-agnostic reusable components to build their Design System component libraries and applications.",
          presenter: "Burton Smith",
          tags: ["Javascript", "Front End", "CSS", "UI/UX"],
          sTime: 10,
          sDay: "Saturday",
          added: false
        },
        {
          id: 4,
          title: "Debugging JavaScript and React",
          desc: "As developers, we spend much of our time debugging apps - often code we didn't even write. Sadly, few developers have ever been taught how to approach debugging - it's something most of us learn through painful experience. The good news is you _can_ learn how to debug effectively, and there's several key techniques and tools you can use for debugging JS and React apps.",
          presenter: "Mark Erikson",
          tags: ["Javascript", "Front End", "React"],
          sTime: 8,
          sDay: "Saturday",
          added: false
        },
        {
          id: 5,
          title: "Accessibility Auditing: Getting Started with Accessibility",
          desc: "This workshop is for people that are just starting or want to get started learning accessibility and how to audit. Or for the people that are in Accessibility that want a refresher or are looking to change their workflows.",
          presenter: "Todd Libby",
          tags: ["Accessibility", "UI/UX"],
          sTime: 8,
          sDay: "Friday",
          added: false
        },
        {
          id: 6,
          title: "Designing Effective Unit Tests for React",
          desc: "React has great tools for Unit Testing component. This does not mean testing is easy. There are still a lot of questions you have to figure out for yourself: How many component tests should you write vs end-to-end tests or lower-level unit tests? How can you test a certain line of code that is tricky to test? And what in the world are you supposed to do about that persistent act() warning?",
          presenter: "Matt Burke",
          tags: ["Front End", "React", "Code Quality"],
          sTime: 13,
          sDay: "Friday",
          added: false
        },
        {
          id: 7,
          title: "Async/Await from the Ground Up",
          desc: "This session is a \"re-introduction\" to async and await. It covers what the keywords mean and - just as importantly - what they *don't* mean. We'll be covering What You Need To Know, including several different conceptual models of async/await that you can switch between at will. This refresher course will take a look at the common async best practices with a careful examination of why they're best practices and when to ignore the best practices. We'll be including some semi-advanced topics (specifically ValueTasks, asynchronous disposal, and Channels) to round out techniques for modern asynchronous development.",
          presenter: "Stephen Cleary",
          tags: ["Front End", "Code Quality"],
          sTime: 15,
          sDay: "Friday",
          added: false
        },
        {
          id: 8,
          title: "Building a Full-Stack Application with Flutter and Dart",
          desc: "For the past few years, Flutter has revolutionized mobile app development by allowing developers to build high-performance, cross-platform applications with ease. However, building a full-stack application can be a challenging task because we often find ourselves juggling multiple technologies to solve problems across an application stack.",
          presenter: "Ryan Edge",
          tags: ["Front End", "Mobile", "Cloud"],
          sTime: 20,
          sDay: "Friday",
          added: false
        },
        {
          id: 9,
          title: "One app, multiple platforms: How Cross Platform Actually Works",
          desc: "Today's solutions for cross platform development all aim to provide developers a better way to build their apps. Build your app in a certain way, and you can ship it to multiple targets (iOS, Android, Web, etc.) with ease. But not all solutions are created equal, and it can be difficult to understand the benefits of one solution over another.",
          presenter: "Mark Erikson",
          tags: ["Javascript", "Mobile"],
          sTime: 15,
          sDay: "Thursday",
          added: false
        },
        {
          id: 10,
          title: "Watch this! Building a Health app for Wear OS",
          desc: "During this talk, we will explore building for this tiny screen using Compose for Wear OS, a declarative framework for creating watch interfaces quickly and easily optimized for the screen shape and size, and the Health Services APIs, an intermediary to the various sensors and algorithms on the watch that provide data related to activity, exercise, and health. With these tools, we will be able to create a beautiful and efficient wear app that can help you track your health goals!",
          presenter: "Sierra OBryan",
          tags: ["Hardware", "Mobile"],
          sTime: 10,
          sDay: "Saturday",
          added: false
        },
      ],
      joined: [
        /* This is an empty array to hold the sessions when they get added */ 
      ]
    };
  },
  methods: {
    showAllSessions() {
      console.log("Test 2")
      document.getElementsByClassName("holder")[0].style.display = "block";
      document.getElementsByClassName("myConferences")[0].style.display = "none";
    },
    showMySessions() {
      console.log("Test 3")
      document.getElementsByClassName("myConferences")[0].style.display = "block";
      document.getElementsByClassName("holder")[0].style.display = "none";
    },
    joinConference(session) {
      console.log("Test 4")
      // Add the selected conference to the joined array
      this.joined.push(session); 
    },
  },
};
</script>
