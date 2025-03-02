<script setup>
import SwiperSlider from "@/components/SwiperSlider.vue";
import ServicesComponent from "~/components/ServicesComponent.vue";
import { onMounted, ref } from "vue";
import gsap from "gsap/dist/gsap";
import ScrollTrigger from "gsap/dist/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

// Refs for animations
const textSection = ref(null);
const heading = ref(null);
const subText = ref(null);
const contactButton = ref(null);
const profileImage = ref(null);
const aboutSection = ref(null);
const skills = ref([]);


onMounted(() => {
  // Timeline animation
  const tl = gsap.timeline({ defaults: { ease: "power3.out" } });

  tl.to(textSection.value, { opacity: 1, y: 0, duration: 1 })
    .from(heading.value, { opacity: 0, y: -20, duration: 0.8 }, "-=0.5")
    .from(subText.value, { opacity: 0, y: 20, duration: 0.8 }, "-=0.5")
    .to(contactButton.value, { opacity: 1, scale: 1, duration: 0.5 }, "-=0.3")
    .to(profileImage.value, { opacity: 1, scale: 1, duration: 1 }, "-=1");
  // About Section Professional Animation
  gsap.from(aboutSection.value, {
    opacity: 0,
    y: 50,
    scale: 0.9,
    duration: 0.6,
    ease: "power2.out",
    scrollTrigger: {
      trigger: aboutSection.value,
      start: "top 75%",
      toggleActions: "play none none reverse"
    }
  });

  onMounted(() => {
    gsap.utils.toArray(skills.value).forEach((skill, index) => {
      gsap.from(skill, {
        opacity: 0,
        y: 30,
        scale: 0.9,
        duration: 0.6,
        delay: index * 0.2,
        ease: "power3.out",
        scrollTrigger: {
          trigger: skill,
          start: "top 85%",
          toggleActions: "play none none reverse",
        },
      });
    });
  });
});


function heroscrollToContact() {
  const contactSection = document.getElementById("contact");
  if (contactSection) {
    contactSection.scrollIntoView({ behavior: "smooth" });
  }
}
</script>
<template>
  <section id="home" ref="heroSection"
    class="container bg-no-repeat bg-center w-full md:h-screen pt-20 overflow-hidden">

    <div class="mx-auto flex flex-col md:flex-row items-center justify-between py-20 h-full relative z-10">
      <!-- Left Side (Text) -->
      <div ref="textSection" class="text-center md:text-left md:w-1/2 opacity-0 translate-y-10">
        <h2 ref="heading" class="text-5xl font-bold text-white">
          Hi, I'm Abdul Wahab
        </h2>
        <p ref="subText" class="text-lg text-white mt-4">
          Shopify developer | Nuxt.js developer
        </p>
        <!-- Get in Touch Button -->
        <button @click="heroscrollToContact" ref="contactButton"
          class="px-7 mt-8 py-3.5 gap-1 transition-all duration-300 bg-blue-600 text-white rounded-full border-2 border-transparent hover:bg-[#040c16] hover:border-white transform scale-90 opacity-0">
          Get in Touch
        </button>
      </div>

      <!-- Right Side (Image) -->
      <div ref="profileImage" class="mt-10 md:mt-0 md:w-1/2 flex justify-center opacity-0 scale-90">
        <img src="@/assets/img/Image.jpg" densities="1x" formate="jpg" alt="Profile Image"
          class="w-64 h-64 md:w-80 md:h-80 rounded-full shadow-lg object-cover" />
      </div>
    </div>
  </section>
  <section id="about" class="bg-black text-white py-20 px-6">
    <div ref="aboutSection" class="md:w-[90%] mx-auto text-center">
      <h2 class="text-lg font-bold text-gray-400 uppercase tracking-wider">Introduction</h2>
      <h3 class="text-5xl font-bold mt-2 text-center">Overview</h3>
      <p class="text-lg mt-4 text-gray-300 text-center">
        I'm a <span class="font-semibold text-white text-center">Shopify Developer</span> with <span
          class="font-semibold text-white">3 years of experience</span> specializing in
        custom theme development and Shopify store optimization.
      </p>
      <p class="text-lg mt-2 text-gray-300 text-center">
        Skilled in <span class="font-semibold text-white">Liquid, HTML, JavaScript, Nuxt.js & TailwindCSS</span>, I
        build high-performance, scalable eCommerce solutions.
      </p>
      <p class="text-lg mt-2 text-gray-300 text-center">
        My goal is to craft seamless online experiences that enhance brand identity and drive conversions.
      </p>
    </div>

    <!-- Skills Grid -->
    <div class="mt-12 md:w-[90%] mx-auto">
      <h3 class="text-3xl font-bold text-center mb-6">What I Do</h3>
      <div class="grid grid-cols-2 lg:grid-cols-4 gap-6">
        <div
          class="bg-[#0D1117] rounded-xl p-6 flex flex-col items-center transform transition-all duration-300 hover:scale-105 hover:shadow-xl hover:shadow-gray-800">
          <img class="transition-transform duration-300 hover:rotate-6" src="/download.png" alt="Frontend Developer">
          <p class="mt-4 font-semibold text-white">Frontend Developer</p>
        </div>
        <div
          class="bg-[#0D1117] rounded-xl p-6 flex flex-col items-center transform transition-all duration-300 hover:scale-105 hover:shadow-xl hover:shadow-gray-800">
          <img class="transition-transform duration-300 hover:rotate-6" src="/icons8-shopify-100.png"
            alt="Shopify Developer">
          <p class="mt-4 font-semibold text-white">Shopify Theme Developer</p>
        </div>
        <div
          class="bg-[#0D1117] rounded-xl p-6 flex flex-col items-center transform transition-all duration-300 hover:scale-105 hover:shadow-xl hover:shadow-gray-800">
          <img class="transition-transform duration-300 hover:rotate-6" src="/icons8-nuxt-js-100.png"
            alt="Nuxt.js Developer">
          <p class="mt-4 font-semibold text-white">Nuxt.js Developer</p>
        </div>
        <div
          class="bg-[#0D1117] rounded-xl p-6 flex flex-col items-center transform transition-all duration-300 hover:scale-105 hover:shadow-xl hover:shadow-gray-800">
          <img class="transition-transform duration-300 hover:rotate-6" src="/icons8-js-100.png" alt="JS Developer">
          <p class="mt-4 font-semibold text-white">JS Developer</p>
        </div>
      </div>
    </div>
  </section>
  <section id="projects" class="p-4 bg-[#0788ff33]" for="Swiper Slider">
    <SwiperSlider />
  </section>
  <section id="services" class="py-16">
    <ServicesComponent />
  </section>
  <section id="services" class="py-16 bg-[#0788ff33]">
    <ExperienceComponent />
  </section>
  <section id="contact" class="py-16 ">
    <ContactComponent />
  </section>
</template>
