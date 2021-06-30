<template>
  <div>
    <div id="content">
      {{ source }}
      <button v-on:click="createPdf">Button</button>
    </div>
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
        short_bio:
          "Alexander A. Apple was born on a cold winter's day in Montana. He is a pretty cool guy who shoots aliens and doesn't afraid of anything.",
        linkedin_url: "linkedin.com/alexaapple",
        twitter_handle: "@realdonaldtrump",
        personal_blog: "myspace.com/alexapple",
        online_resume_url: "livejournal.com/alexapple",
        github_url: "github.com/alexapple",
        photo: "https://informationcradle.com/wp-content/uploads/2020/05/5a3d391bd0e56.image-1.jpg",
        experiences: [
          {
            start_date: "March 7, 2018",
            end_date: null,
            job_title: "Actor",
            company_name: "AAA Theatre Productions",
            details: "Produced a live stage version of Edward Scissorhands",
          },
          {
            start_date: "March 7, 2015",
            end_date: "March 7, 2018",
            job_title: "Insurance Salesman",
            company_name: "Evil Corp",
            details: "Sold life, boat, volcano insurance policies.",
          },
        ],
        educations: [
          {
            start_date: "August 5, 2013",
            end_date: "May 28, 2015",
            degree: "Art History",
            university_name: "Harvard",
            details: "I went to harvard btw",
          },
          {
            start_date: "August 7, 2011",
            end_date: "May 9, 2012",
            degree: "Art Prehistory",
            university_name: "Boston Community College",
            details: "didn't want to get in too much harvard debt lol",
          },
        ],
      },
    };
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
      doc.setFontSize(5);
      doc.text(20, 45, "Short Bio");
      doc.text(20, 50, this.source.short_bio);
      doc.text(20, 60, this.source.linkedin_url);
      doc.text(20, 70, this.source.twitter_handle);
      doc.text(20, 80, this.source.personal_blog);
      doc.text(20, 90, this.source.online_resume_url);
      doc.text(20, 100, this.source.github_url);
      doc.text(20, 110, this.source.photo);
      // doc.text(20, 20, this.source.experiences);
      // doc.text(20, 30, "This is client-side Javascript to generate a PDF.");

      // Add new page
      doc.addPage();
      // doc.text(20, 20, "Visit semicolonworld.com");

      // Save the PDF
      doc.save("document.pdf");
    },
  },
};
</script>
