<template>
  <div class="container">
    <!-- Click Counter -->
    <section class="section">
      <h1 class="title">Click Counter</h1>
      <p class="counter-text">Button clicked: <span class="highlight">{{ count }}</span> times</p>
      <button class="btn-primary" @click="incrementCounter">Click me</button>
    </section>

    <!-- Box Color Change -->
    <section class="section">
      <h1 class="title">Change Box Color</h1>
      <div :style="{ backgroundColor: currentColor }" class="color-box">
        <p class="color-text">{{ currentColor }}</p>
      </div>
      <button class="btn-primary" @click="changeColor">Change Color</button>
    </section>

    <!-- Image Carousel -->
    <section class="section">
      <h1 class="title">Image Carousel</h1>
      <div class="carousel">
        <img :src="images[currentImage]" alt="Image Carousel" class="carousel-image" />
        <div class="carousel-controls">
          <button class="btn-secondary" @click="prevImage">Previous</button>
          <button class="btn-secondary" @click="nextImage">Next</button>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      colors: ['#e63946', '#457b9d', '#2a9d8f', '#f4a261', '#6d597a'], // Modern hex color values
      currentColor: '#e63946',
      currentImage: 0,
      images: [
        'https://i.pinimg.com/564x/aa/72/91/aa72913855f9e02a949a5c392b48299e.jpg',
        'https://i.pinimg.com/564x/c1/fd/ab/c1fdab61de37aebb6a189c6d0880e8d6.jpg',
      ]
    };
  },
  methods: {
    incrementCounter() {
      this.count++;
    },
    changeColor() {
      const randomIndex = Math.floor(Math.random() * this.colors.length);
      this.currentColor = this.colors[randomIndex];
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    },
    prevImage() {
      this.currentImage = (this.currentImage - 1 + this.images.length) % this.images.length;
    }
  }
};
</script>

<style>
/* Global Styles */
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
  font-family: 'Arial', sans-serif;
}

.section {
  margin-bottom: 40px;
}

.title {
  font-size: 2em;
  margin-bottom: 20px;
  color: #f7f7f7;
}

.counter-text,
.color-text {
  font-size: 1.2em;
  margin: 10px 0;
}

.highlight {
  color: #e63946;
  font-weight: bold;
}

.color-box {
  width: 150px;
  height: 150px;
  margin: 20px auto;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  color: white;
  font-size: 1.5em;
  text-transform: uppercase;
  font-weight: bold;
}

/* Button Styles */
button {
  cursor: pointer;
  border: none;
  padding: 12px 24px;
  border-radius: 8px;
  font-size: 1em;
  transition: background-color 0.3s ease;
}

.btn-primary {
  background-color: #457b9d;
  color: white;
}

.btn-primary:hover {
  background-color: #1d3557;
}

.btn-secondary {
  background-color: #f4a261;
  color: white;
}

.btn-secondary:hover {
  background-color: #e76f51;
}

/* Carousel Styles */
.carousel {
  display: flex;
  flex-direction: column;
  align-items: center; /* Centers the image and controls horizontally */
  margin: 20px auto;
  position: relative;
}

.carousel-image {
  width: 100%;
  max-width: 400px;
  height: auto;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.carousel-controls {
  display: flex;
  justify-content: center; /* Centers the buttons horizontally */
  margin-top: 20px;
}

.carousel-controls button {
  margin: 0 10px;
}

@media (max-width: 600px) {
  .container {
    padding: 10px;
  }

  .carousel-image {
    width: 100%;
  }
}
</style>
