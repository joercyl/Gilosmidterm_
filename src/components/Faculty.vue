<template>
  <section id="faculty" class="faculty-section">
    <div class="section-heading">
      <p>THE PEOPLE BEHIND CCS</p>
      <h2>Faculty & Staff</h2>
      <div class="heading-line"></div>
      <span>
        Meet the leaders, educators, and staff who support the CCS community.
      </span>
    </div>

    <section
      v-for="group in facultyGroups"
      :key="group.title"
      class="directory-group"
      :class="{ 'directory-group-centered': ['Dean', 'Department Heads', 'Program Coordinators'].includes(group.title) }"
    >
      <div class="department-heading">
        <div>
          <p>CCS DIRECTORY</p>
          <h3>{{ group.title }}</h3>
        </div>
      </div>

      <div v-if="group.people.length" class="faculty-grid">
        <article
          v-for="person in group.people"
          :key="person.name"
          class="faculty-card"
        >
          <div class="faculty-image">
            <img
              v-if="person.photo"
              :src="person.photo"
              :alt="person.name"
              @error="imageError"
            />
            <div v-else class="faculty-image-placeholder" aria-hidden="true">
              {{ person.initials }}
            </div>
          </div>

          <div class="faculty-info">
            <span>{{ person.position }}</span>
            <h4>{{ person.name }}</h4>
            <p v-if="person.education">{{ person.education }}</p>
          </div>
        </article>
      </div>
      <p v-else class="directory-placeholder">
        Profile information and photo will be added.
      </p>
    </section>
  </section>
</template>

<script setup lang="ts">

import LPBPhoto from '../assets/images/LPB.jpg'
import AMMPhoto from '../assets/images/AMM.jpg'
import AMPPhoto from '../assets/images/AMP.jpg'
import chriseldaPhoto from '../assets/images/Chriselda.jpg'
import CCCPhoto from '../assets/images/CCC.jpg'
import RCEPhoto from '../assets/images/RCE.jpg'
import rosePhoto from '../assets/images/Rose.jpg'
import donnaPhoto from '../assets/images/donna.jpg'
import quijanoPhoto from '../assets/images/quijano.png'
import balontongPhoto from '../assets/images/balontong.jpg'
import cantelPhoto from '../assets/images/cantel.jpg'
import parrenoPhoto from '../assets/images/parreno.jpg'

interface FacultyMember {
  name: string
  position: string
  education?: string
  photo?: string
  initials?: string
}

const dean: FacultyMember[] = [
  {
    name: 'Ma. Christina A. Quijano',
    position: 'Dean',
    education: 'MSCS',
    photo: quijanoPhoto
  }
]

const departmentHeads: FacultyMember[] = [
  {
    name: 'Rea P. Balontong',
    position: 'Department Head (IT & IS)',
    education: 'MBA',
    photo: balontongPhoto
  }
]

const programCoordinators: FacultyMember[] = [
  {
    name: 'Marjee Rose B. Parreño',
    position: 'Program Coordinator (BSCS, BSDMIA, and MSCS)',
    education: 'MSCS, MBA',
    photo: parrenoPhoto
  },
  {
    name: 'Ana Mae B. Cantel',
    position: 'Program Coordinator (BLIS and MLIS)',
    education: 'MLIS',
    photo: cantelPhoto
  }
]

const faculty: FacultyMember[] = [
  {
    name: 'Leo Paulo B. Beldia',
    position: 'Faculty Member',
    photo: LPBPhoto
  },
  {
    name: 'Antonio M. Montano',
    position: 'Faculty Member',
    photo: AMMPhoto
  },
  {
    name: 'A.M.P Latter P. Taasan',
    position: 'Faculty Member',
    photo: AMPPhoto
  },
  {
    name: 'Chriselda Elaine Ador',
    position: 'Faculty Member',
    photo: chriseldaPhoto
  },
  {
    name: 'Chrislyn C. Castano',
    position: 'Faculty Member',
    photo: CCCPhoto
  },
  {
    name: 'Rodolfo C. Eregia Jr.',
    position: 'Faculty Member',
    photo: RCEPhoto
  },
  {
    name: 'Rose Leah Joy A. Ojacastro',
    position: 'Faculty Member',
    photo: rosePhoto
  },
  {
    name: 'Donna May Rivera',
    position: 'Faculty Member',
    photo: donnaPhoto
  }
]

const facultyGroups: { title: string; people: FacultyMember[] }[] = [
  { title: 'Dean', people: dean },
  { title: 'Department Heads', people: departmentHeads },
  { title: 'Program Coordinators', people: programCoordinators },
  { title: 'Faculty', people: faculty }
]

const imageError = (event: Event) => {
  const image = event.target as HTMLImageElement

  image.style.display = 'none'
}

</script>

<style scoped>
.faculty-section {
  padding: 120px 5%;

  background: #f8faf5;
}

.section-heading {
  max-width: 850px;

  margin: 0 auto 80px;

  text-align: center;
}

.section-heading p {
  color: #287b45;

  font-size: 14px;
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
  color: #777;

  font-size: 17px;
  line-height: 1.8;
}

.directory-group {
  width: min(1400px, 100%);

  margin: 0 auto 90px;
}

.department-heading {
  display: flex;
  align-items: center;

  gap: 20px;

  margin-bottom: 35px;
}

.directory-group-centered .department-heading {
  justify-content: center;
  text-align: center;
}

.department-heading p {
  margin: 0;

  color: #999;

  font-size: 11px;
  letter-spacing: 3px;
  font-weight: 700;
}

.department-heading h3 {
  margin: 5px 0 0;

  color: #20372c;

  font-size: 30px;
}

.directory-placeholder {
  margin: 0;
  padding: 30px;
  border: 1px dashed rgba(40, 123, 69, 0.3);
  border-radius: 6px;
  color: #69766d;
  text-align: center;
}

.faculty-grid {
  display: grid;

  grid-template-columns: repeat(4, 1fr);

  gap: 25px;
}

.directory-group-centered .faculty-grid {
  grid-template-columns: repeat(auto-fit, minmax(min(100%, 280px), 320px));
  justify-content: center;
}

.faculty-card {
  overflow: hidden;

  background: #f8f8f6;

  border-radius: 6px;

  transition: 0.3s ease;
}

.faculty-card:hover {
  transform: translateY(-8px);

  box-shadow: 0 18px 35px rgba(0, 0, 0, 0.12);
}

.faculty-image {
  height: 300px;

  display: flex;
  justify-content: center;
  align-items: center;

  overflow: hidden;

  background:
    linear-gradient(
      135deg,
      #b0bbbb,
      #edf1f1
    );
}

.faculty-image img {
  width: 100%;
  height: 100%;

  object-fit: cover;
}

.faculty-image-placeholder {
  width: 100%;
  height: 100%;
  display: grid;
  place-items: center;
  background:
    radial-gradient(circle at 50% 35%, rgba(244, 165, 28, 0.2), transparent 28%),
    linear-gradient(135deg, #e8efe4, #d8e5d3);
  color: #287b45;
  font-size: 64px;
  font-weight: 800;
  letter-spacing: 2px;
}

.faculty-info {
  padding: 25px;
}

.faculty-info span {
  color: #c47a08;

  font-size: 11px;

  font-weight: 800;

  text-transform: uppercase;

  letter-spacing: 1px;
}

.faculty-info h4 {
  margin: 8px 0;

  color: #20372c;

  font-size: 20px;
}

.faculty-info p {
  margin: 0;

  color: #888;

  font-size: 14px;

  line-height: 1.6;
}

@media (max-width: 1100px) {
  .faculty-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .faculty-section {
    padding: 80px 6%;
  }

  .faculty-grid {
    grid-template-columns: 1fr;
  }

  .faculty-image {
    height: 350px;
  }

  .department-heading h3 {
    font-size: 23px;
  }
}
</style>