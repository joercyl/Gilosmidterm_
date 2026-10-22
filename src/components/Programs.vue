<template>
  <section id="programs" class="programs-section">
    <div class="section-heading">
      <p>ACADEMIC PROGRAMS</p>

      <h2>Programs Offered</h2>

      <div class="heading-line"></div>

      <span>
        Discover the academic programs offered by the College of Computer Studies
        and explore pathways to a future in technology.
      </span>
    </div>

    <div class="programs-container">
      <article
        v-for="program in programs"
        :key="program.name"
        class="program-card"
      >
        <div class="program-logo">
          <img
            :src="program.logo"
            :alt="`${program.name} logo`"
            @error="imageError"
          />

        </div>

        <span class="program-code">
          {{ program.shortName }}
        </span>

        <h3>{{ program.name }}</h3>

        <p>
          {{ program.description }}
        </p>
      </article>
    </div>
  </section>
</template>

<script setup lang="ts">
import Itso from '../assets/images/itso.png'
import ccs from '../assets/images/css.png'
import midas from '../assets/images/midas.png'
import lis from '../assets/images/lisso.jpeg'

interface Program {
  name: string
  shortName: string
  description: string
  logo: string
}

const programs: Program[] = [
  {
    name: 'Information Technology',
    shortName: 'BSIT',
    description:
      'The Bachelor of Science in Information Technology program develops practical skills in software development, information systems, networking, databases, and modern technologies.',
    logo: Itso
  },
  {
    name: 'Computer Science',
    shortName: 'BSCS',
    description:
      'The Bachelor of Science in Computer Science program focuses on computing concepts, algorithms, programming, software development, and computer systems.',
    logo: ccs
  },
  {
    name: 'Digital Media and Interactive Arts',
    shortName: 'BSDMIA',
    description:
      'The Bachelor of Science in Digital Media and Interactive Arts program combines creativity and technology through digital media, multimedia, interactive design, and emerging technologies.',
    logo: midas
  },
  {
    name: 'Library and Information Science',
    shortName: 'BLIS',
    description:
      'The Bachelor of Library and Information Science program prepares students in information organization, management, research, digital resources, and library services.',
    logo: lis
  }
]

const imageError = (event: Event) => {
  const image = event.target as HTMLImageElement

  image.style.display = 'none'
}
</script>

<style scoped>
.programs-section {
  padding: 120px 5%;
  background: #f8faf5;

}

.section-heading {
  max-width: 850px;

  margin: 0 auto 70px;

  text-align: center;
}

.section-heading p {
  color: #287b45;

  font-size: 13px;
  font-weight: 800;

  letter-spacing: 3px;
}

.section-heading h2 {
  margin: 10px 0;

  color: #20372c;

  font-size: clamp(38px, 5vw, 58px);
}

.heading-line {
  width: 60px;
  height: 4px;

  margin: 20px auto;

  background: #f4a51c;
}

.section-heading span {
  color: #777777;

  font-size: 17px;

  line-height: 1.8;
}

.programs-container {
  width: min(1300px, 100%);

  margin: auto;

  display: grid;

  grid-template-columns: repeat(4, 1fr);

  gap: 25px;
}

.program-card {
  min-height: 450px;

  padding: 35px 28px;

  display: flex;
  flex-direction: column;
  align-items: center;

  text-align: center;

  background: #ffffff;

  border: 1px solid #e5e5e5;

  border-radius: 8px;

  box-shadow:
    0 10px 30px rgba(0, 0, 0, 0.07);

  transition: 0.3s ease;
}

.program-card:hover {
  transform: translateY(-8px);

  border-color: #f4a51c;

  box-shadow:
    0 18px 40px rgba(0, 0, 0, 0.12);
}

.program-logo {
  position: relative;

  width: 140px;
  height: 140px;

  margin-bottom: 20px;

  display: flex;
  align-items: center;
  justify-content: center;
}

.program-logo img {
  max-width: 100%;
  max-height: 100%;

  object-fit: contain;
}



.program-code {
  margin-bottom: 10px;

  color: #c47a08;

  font-size: 12px;

  font-weight: 800;

  letter-spacing: 2px;
}

.program-card h3 {
  min-height: 60px;

  margin: 0 0 18px;

  color: #20372c;

  font-size: 23px;

  line-height: 1.3;
}

.program-card p {
  color: #777777;

  font-size: 14px;

  line-height: 1.8;
}

@media (max-width: 1050px) {
  .programs-container {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 650px) {
  .programs-section {
    padding: 120px 5%;
  }

  .programs-container {
    grid-template-columns: 1fr;
  }

  .program-card {
    min-height: auto;
  }
}
</style>