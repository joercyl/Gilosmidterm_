<script setup>
import ccsLogo from '../assets/images/ccs2.png'
import heroBg from '../assets/images/bg.jpg'
</script>

<template>
  <section
    id="home"
    class="hero"
    :style="{ '--bg': `url(${heroBg})` }"
  >
    <div class="hero-container">
      <div class="hero-content">
        <p class="hero-eyebrow">
          <span></span>
          College of Computer Studies
        </p>

        <h1>
          Home of the
          <span>Dauntless</span>
          <span class="hero-title-last">and the Brave.</span>
        </h1>

        <p class="hero-tagline">Different people. <strong>One goal.</strong></p>

        <p class="hero-description">
          Discover your potential, create with purpose, and shape what comes
          next in technology.
        </p>

        <RouterLink to="/#programs" class="hero-button">
          Explore our programs
          <span aria-hidden="true">→</span>
        </RouterLink>

        <p class="hero-university">Central Philippine University</p>
      </div>

      <div class="hero-visual" aria-label="College of Computer Studies emblem">
        <div class="visual-orbit visual-orbit-one"></div>
        <div class="visual-orbit visual-orbit-two"></div>
        <div class="visual-accent"></div>
        <div class="hero-logo">
          <img :src="ccsLogo" alt="College of Computer Studies emblem" />
        </div>
      </div>
    </div>

    <a class="hero-scroll" href="#programs" aria-label="Scroll to programs">
      <span>SCROLL TO EXPLORE</span>
      <span class="scroll-line" aria-hidden="true"></span>
    </a>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  isolation: isolate;
  min-height: max(760px, 100svh);
  overflow: hidden;
  display: flex;
  align-items: center;
  padding: 115px 0 90px;
  background:
    radial-gradient(ellipse at 82% 48%, rgba(133, 195, 66, 0.12), transparent 38%),
    #f8faf5;
}

.hero::before {
  position: absolute;
  z-index: -1;
  inset: 0;
  content: "";
  background-image:
    linear-gradient(90deg, rgba(248, 250, 245, 0.96) 0%, rgba(248, 250, 245, 0.8) 48%, rgba(248, 250, 245, 0.42) 100%),
    var(--bg);
  background-position: center, left center;
  background-size: cover;
  opacity: 0.58;
}

.hero-container {
  width: min(1280px, 88%);
  margin: 0 auto;
  display: grid;
  grid-template-columns: minmax(0, 1.1fr) minmax(320px, 0.9fr);
  align-items: center;
  gap: clamp(40px, 8vw, 120px);
}

.hero-content {
  max-width: 680px;
  padding: 25px 0;
}

.hero-eyebrow {
  display: flex;
  align-items: center;
  gap: 12px;
  margin: 0 0 24px;
  color: #426343;
  font-size: 12px;
  font-weight: 800;
  letter-spacing: 2.8px;
  text-transform: uppercase;
}

.hero-eyebrow span {
  width: 34px;
  height: 2px;
  background: #f4a51c;
}

.hero h1 {
  margin: 0;
  color: #20372c;
  font-family: 'Montserrat', 'Inter', sans-serif;
  font-size: clamp(54px, 7vw, 92px);
  font-weight: 800;
  letter-spacing: -5px;
  line-height: 0.98;
}

.hero h1 > span {
  display: block;
  color: #287b45;
}

.hero h1 .hero-title-last {
  color: #20372c;
}

.hero-tagline {
  margin: 30px 0 12px;
  color: #596b5e;
  font-size: clamp(19px, 2vw, 24px);
  letter-spacing: 0.3px;
}

.hero-tagline strong {
  color: #d78a0a;
}

.hero-description {
  max-width: 510px;
  margin: 0;
  color: #69766d;
  font-size: 16px;
  line-height: 1.8;
}

.hero-button {
  display: inline-flex;
  align-items: center;
  gap: 22px;
  margin-top: 34px;
  padding: 16px 22px 16px 25px;
  border: 1px solid #246b3e;
  border-radius: 4px;
  background: #246b3e;
  box-shadow: 0 10px 24px rgba(36, 107, 62, 0.16);
  color: #ffffff;
  font-size: 14px;
  font-weight: 700;
  text-decoration: none;
  transition: background 0.2s ease, color 0.2s ease, transform 0.2s ease, box-shadow 0.2s ease;
}

.hero-button span {
  color: #ffc04b;
  font-size: 20px;
  line-height: 1;
  transition: transform 0.2s ease;
}

.hero-button:hover {
  transform: translateY(-3px);
  background: #1b5632;
  box-shadow: 0 14px 28px rgba(36, 107, 62, 0.24);
}

.hero-button:hover span {
  transform: translateX(4px);
}

.hero-university {
  margin: 28px 0 0;
  color: #718074;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 1.2px;
  text-transform: uppercase;
}

.hero-visual {
  position: relative;
  width: min(100%, 480px);
  aspect-ratio: 1;
  justify-self: end;
  display: grid;
  place-items: center;
  isolation: isolate;
}

.hero-visual::before {
  position: absolute;
  z-index: -1;
  inset: 8%;
  content: "";
  border: 1px solid rgba(40, 123, 69, 0.18);
  border-radius: 50%;
  background:
    radial-gradient(circle at 35% 28%, #ffffff 0%, #f3f7eb 54%, #e7efdd 100%);
  box-shadow: 0 30px 80px rgba(40, 75, 48, 0.12);
}

.hero-logo {
  width: 57%;
  aspect-ratio: 1;
  display: grid;
  place-items: center;
  border: 1px solid rgba(40, 123, 69, 0.12);
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.72);
  box-shadow: 0 14px 45px rgba(32, 55, 44, 0.1);
}

.hero-logo img {
  width: 73%;
  height: 73%;
  object-fit: contain;
}

.visual-orbit {
  position: absolute;
  border: 1px solid rgba(40, 123, 69, 0.2);
  border-radius: 50%;
}

.visual-orbit-one {
  inset: 1%;
}

.visual-orbit-two {
  inset: 15%;
  border-style: dashed;
  border-color: rgba(244, 165, 28, 0.38);
}

.visual-accent {
  position: absolute;
  top: 15%;
  right: 13%;
  width: 19px;
  height: 19px;
  border: 4px solid #f4a51c;
  border-radius: 50%;
  background: #f8faf5;
  box-shadow: 0 0 0 8px rgba(244, 165, 28, 0.12);
}

.hero-scroll {
  position: absolute;
  bottom: 27px;
  left: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  transform: translateX(-50%);
  color: #647568;
  text-decoration: none;
}

.hero-scroll > span:first-child {
  font-size: 9px;
  font-weight: 700;
  letter-spacing: 2px;
}

.scroll-line {
  width: 1px;
  height: 28px;
  background: #e3a12a;
}

@media (max-width: 900px) {
  .hero {
    min-height: 100svh;
    padding: 110px 0 80px;
  }

  .hero-container {
    grid-template-columns: minmax(0, 1fr) minmax(250px, 0.8fr);
    gap: 32px;
  }

  .hero h1 {
    font-size: clamp(50px, 8vw, 70px);
    letter-spacing: -3px;
  }

  .hero-visual {
    width: 100%;
  }
}

@media (max-width: 650px) {
  .hero {
    min-height: auto;
    padding: 120px 0 86px;
  }

  .hero::before {
    background-image:
      linear-gradient(180deg, rgba(248, 250, 245, 0.88), rgba(248, 250, 245, 0.96)),
      var(--bg);
    background-position: center, left center;
  }

  .hero-container {
    width: min(520px, 88%);
    grid-template-columns: 1fr;
    gap: 28px;
  }

  .hero-content {
    padding: 0;
    text-align: center;
  }

  .hero-eyebrow {
    justify-content: center;
    margin-bottom: 18px;
    font-size: 10px;
    letter-spacing: 2px;
  }

  .hero h1 {
    font-size: clamp(47px, 13vw, 68px);
    letter-spacing: -3px;
  }

  .hero-tagline {
    margin-top: 22px;
  }

  .hero-description {
    margin: 0 auto;
    font-size: 14px;
  }

  .hero-button {
    margin-top: 26px;
  }

  .hero-university {
    margin-top: 20px;
    font-size: 10px;
  }

  .hero-visual {
    width: min(68vw, 290px);
    justify-self: center;
  }

  .hero-scroll {
    bottom: 15px;
  }
}

@media (prefers-reduced-motion: reduce) {
  .hero-button,
  .hero-button span {
    transition: none;
  }
}
</style>
