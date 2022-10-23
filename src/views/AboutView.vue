<template>
  <div class="about">
    <h1 class="about-header">About Us</h1>
    <p>
      Newscaster keeps you updated with the latest happenings in Nigeria by  collating news
      from different media houses and sources. Please note, we do not verify the information gotten from these sources,
     however, we try to regulate misinformation by pulling data from only reputable sources.
    </p>
    <p>To find out more about us, kindly visit <a href="https://philians.com" target="_blank">https://philians.com </a>and for inquires, projects or consultations, please send an email to danie@philians.com</p>
    <p>
      This application was built with Vue Js 3 and it was inspired by Damilare
      Ademeso.
    </p>
  </div>
</template>

<style scoped>
@media (min-width: 1024px) {}


.about{
  margin: 10px auto; 
  padding: 3rem 0; 
  max-width: 70%
}
.about-header {
  font-size: 4rem;
  font-weight: 800;
  color: #001529;
}

p {
  color: #001529;
  font-weight: 500;
}
@media screen and (max-width: 600px) {
  .about{max-width: 100%}
  .about-header {
  font-size: 2rem;
}
}
</style>
