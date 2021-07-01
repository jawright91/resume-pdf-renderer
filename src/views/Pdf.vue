<template>
  <div>
    <div id="content">
      <p>Select Whose Resume to convert to PDF:</p>
      <select v-model="source">
        <option v-for="student in students" :value="student" v-bind:key="student.id">
          {{ student.first_name }} {{ student.last_name }}
        </option>
      </select>
      <h2>Biographical Information</h2>
      <p>
        First Name:
        <input v-model="source.first_name" />
      </p>
      <p>
        Last Name:
        <input v-model="source.last_name" />
      </p>
      <p>
        Email:
        <input v-model="source.email" />
      </p>
      <p>
        Phone Number:
        <input v-model="source.phone_number" />
      </p>
      <p>
        Short Biography:
        <input v-model="source.bio" />
      </p>
      <p>
        LinkedIn URL:
        <input v-model="source.linkedin" />
      </p>
      <p>
        Twitter Handle:
        <input v-model="source.twitter_handle" />
      </p>
      <p>
        Personal Blog:
        <input v-model="source.website" />
      </p>
      <p>
        Online Resume URL:
        <input v-model="source.resume_url" />
      </p>
      <p>
        Github URL:
        <input v-model="source.github" />
      </p>
      <p>
        Photo URL:
        <input v-model="source.photo" />
      </p>
      <h2>Experience</h2>
      <div class="experiences" v-for="experience in source.experiences" v-bind:key="experience.id">
        <h3>{{ experience.job_title }} at {{ experience.company_name }}</h3>
        <p>
          Start Date:
          <input v-model="experience.start_date" />
        </p>
        <p>
          End Date:
          <input v-model="experience.end_date" />
        </p>
        <p>
          Job Title:
          <input v-model="experience.job_title" />
        </p>
        <p>
          Company Name:
          <input v-model="experience.company_name" />
        </p>
        <p>
          Details:
          <input v-model="experience.details" />
        </p>
      </div>
    </div>
    <h2>Eductaion</h2>
    <div class="education" v-for="education in source.educations" v-bind:key="education.id">
      <h3>{{ education.degree }} at {{ education.university_name }}</h3>
      <p>
        Start Date:
        <input v-model="education.start_date" />
      </p>
      <p>
        End Date:
        <input v-model="education.end_date" />
      </p>
      <p>
        Job Title:
        <input v-model="education.degree" />
      </p>
      <p>
        Company Name:
        <input v-model="education.university_name" />
      </p>
      <p>
        Details:
        <input v-model="education.details" />
      </p>
    </div>
    <button v-on:click="createPdf">Create PDF</button>
    <div id="elementH"></div>
  </div>
</template>
<style></style>
<script>
// eslint-disable-next-line no-unused-vars
import jsPDF from "jspdf";
// eslint-disable-next-line no-unused-vars
import jquery from "jquery";
// eslint-disable-next-line no-unused-vars
import axios from "axios";

export default {
  setup() {},
  data: function () {
    return {
      source: {
        first_name: "Alex",
        last_name: "Apple",
        email: "alex@example.com",
        phone_number: "8675309",
        bio: "Alexander A. Apple was born on a cold winter's day in Montana. He is a pretty cool guy who shoots aliens and doesn't afraid of anything.",
        linkedin: "linkedin.com/alexaapple",
        twitter_handle: "@realdonaldtrump",
        website: "myspace.com/alexapple",
        resume_url: "livejournal.com/alexapple",
        github: "github.com/alexapple",
        photo: "https://informationcradle.com/wp-content/uploads/2020/05/5a3d391bd0e56.image-1.jpg",
        experiences: [
          {
            id: 1,
            start_date: "March 7, 2018",
            end_date: null,
            job_title: "Actor",
            company_name: "AAA Theatre Productions",
            details: "Produced a live stage version of Edward Scissorhands",
          },
          {
            id: 2,
            start_date: "March 7, 2015",
            end_date: "March 7, 2018",
            job_title: "Insurance Salesman",
            company_name: "Evil Corp",
            details: "Sold life, boat, volcano insurance policies.",
          },
        ],
        educations: [
          {
            id: 1,
            start_date: "August 5, 2013",
            end_date: "May 28, 2015",
            degree: "Art History",
            university_name: "Harvard",
            details: "I went to harvard btw",
          },
          {
            id: 2,
            start_date: "August 7, 2011",
            end_date: "May 9, 2012",
            degree: "Art Prehistory",
            university_name: "Boston Community College",
            details: "didn't want to get in too much harvard debt lol",
          },
        ],
      },
      students: [],
    };
  },
  created: function () {
    this.indexStudents();
  },
  methods: {
    createPdf() {
      var doc = new jsPDF({
        orientation: "portrait",
      });
      doc.setFontSize(24);
      doc.text(
        `${this.source.first_name} ${this.source.last_name}`,
        doc.internal.pageSize.getWidth() / 2,
        10,
        null,
        null,
        "center"
      );
      doc.setFontSize(10);
      doc.text(this.source.email, doc.internal.pageSize.getWidth() / 2, 15, null, null, "center");
      doc.text(this.source.phone_number, doc.internal.pageSize.getWidth() / 2, 20, null, null, "center");
      doc.setFontSize(15);
      var linecoordinate = 45;
      doc.text(20, linecoordinate, "Short Bio:");
      linecoordinate += 5;
      doc.setFontSize(7);
      doc.text(20, linecoordinate, this.source.bio);
      doc.setFontSize(15);
      linecoordinate += 10;
      doc.text(20, linecoordinate, "Linkedin URL");
      doc.setFontSize(5);
      linecoordinate += 5;
      doc.text(20, linecoordinate, this.source.linkedin);
      doc.setFontSize(15);
      linecoordinate += 10;
      doc.text(20, linecoordinate, "Twitter Handle:");
      linecoordinate += 5;
      doc.setFontSize(10);
      doc.text(20, linecoordinate, this.source.twitter_handle);
      doc.setFontSize(15);
      linecoordinate += 5;
      doc.text(20, linecoordinate, "Personal Blog");
      linecoordinate += 5;
      doc.text(20, linecoordinate, this.source.website);
      doc.setFontSize(15);
      linecoordinate += 5;
      doc.text(20, linecoordinate, "Online Resume URL");
      linecoordinate += 5;
      doc.text(20, linecoordinate, this.source.resume_url);
      doc.setFontSize(10);
      linecoordinate += 5;
      doc.text(20, linecoordinate, "Github URL");
      linecoordinate += 5;
      doc.text(20, linecoordinate, this.source.github);
      doc.setFontSize(15);
      linecoordinate += 5;
      doc.text(20, linecoordinate, this.source.photo);
      linecoordinate += 5;
      // doc.text(20, linecoordinate, this.source.experiences);
      this.source.experiences.forEach((experience) => {
        doc.text(20, linecoordinate, experience.company_name);
        linecoordinate += 5;
      });
      // Add new page
      doc.addPage();
      // doc.text(20, 20, "Visit semicolonworld.com");
      // Save the PDF
      doc.save("document.pdf");
    },
    indexStudents: function () {
      axios.get("https://guarded-ridge-08594.herokuapp.com/students").then((response) => {
        this.students = response.data;
        console.log("hey ", this.students);
      });
    },
    makeActive(selection) {
      this.source = selection;
    },
  },
};
</script>
