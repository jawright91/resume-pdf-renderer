<template>
  <div></div>
</template>
<style></style>
<script>
// eslint-disable-next-line no-unused-vars
import jspdf from "jspdf";
// eslint-disable-next-line no-unused-vars
import jquery from "jquery";

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
        experience: [
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
            job_title: "Janitor/Insurance Salesman",
            company_name: "Evil Corp",
            details: "Sold life, boat, volcano insurance policies. Oversaw sanitation of headquarters.",
          },
        ],
        education: [
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
};
</script>
