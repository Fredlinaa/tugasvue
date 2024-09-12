<template>
  <div id="app">
 
    <header>
      <h1>Lana Del Rey</h1>
      <p>Say Yes To Heaven Mrs Dp.</p>
    </header>

    <main>
      <div class="section counter-section">
        <div class="section-header">
          <h2>Button</h2>
        </div>
        <p class="counter-text">Clicked: <strong>{{ counter }}</strong> times</p>
        <button @click="incrementCounter">Click Me!</button>
      </div>

      <div class="section color-changer-section">
        <div class="section-header">
          <h2>Colors</h2>
        </div>
        <div :style="{ backgroundColor: currentColor }" class="color-box"></div>
        <button @click="changeColor">Change Color</button>
      </div>

      <div class="section carousel-section">
        <div class="section-header">
          <h2>Photos</h2>
        </div>
        <div class="carousel">
          <img :src="images[currentImageIndex]" alt="Image Carousel" />
          <p class="carousel-caption">{{ captions[currentImageIndex] }}</p>
          <div class="carousel-controls">
            <button @click="prevImage">Prev</button>
            <button @click="nextImage">Next</button>
          </div>
        </div>
      </div>
    </main>

  </div>

  <footer>
    <p>&copy; TUGAS FRAMEWORK T3G, Fredlina Devhania.</p>
  </footer>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      counter: 0,
      colors: ['#D0B9A2', '#C5A67A', '#B89A6A', '#C0A080', '#E6B99A'],
      currentColorIndex: 0,
      images: [
        require('@/assets/lana1.jpg'),
        require('@/assets/lana2.jpg'),
        require('@/assets/lana3.jpg')
      ],

      captions: [
        '“Who are you?”',
        '“Live fast. Die young. Be wild. Have fun.”',
        '“And I still love him. I love him.”'
      ],
      currentImageIndex: 0
    };
  },
  computed: {
    currentColor() {
      return this.colors[this.currentColorIndex];
    }
  },
  methods: {
    incrementCounter() {
      this.counter++;
    },
    changeColor() {
      this.currentColorIndex = (this.currentColorIndex + 1) % this.colors.length;
    },
    nextImage() {
      this.currentImageIndex = (this.currentImageIndex + 1) % this.images.length;
    },
    prevImage() {
      this.currentImageIndex = (this.currentImageIndex - 1 + this.images.length) % this.images.length;
    }
  }
};
</script>

<style>
 
 body {
  font-family: 'Lora', serif;
  background: linear-gradient(135deg, #f7f7f7, #e0e0e0); 
  color: #333; 
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  box-sizing: border-box;
}

header {
  text-align: center;
  margin: 40px 20px;
}

h1 {
  font-family: 'Playfair Display', serif;
  color: #B57B5E; 
  margin-bottom: 10px;
  font-size: 48px;
  text-shadow: 3px 3px 8px rgba(181, 123, 94, 0.3);
}

p {
  font-size: 20px;
  color: #6c6c6c;
}

main {
  max-width: 1200px;
  padding: 20px;
  border-radius: 15px;
  background: #ffffff;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
  text-align: center;
  margin-bottom: 40px;
}

.section {
  margin: 30px 0;
  padding: 20px;
  background: rgba(255, 255, 255, 0.9);
  border-radius: 12px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
  max-width: 100%;
  overflow: hidden;
}

.section-header {
  background: linear-gradient(135deg, #C5A67A, #E6B99A);
  padding: 12px 20px;
  border-radius: 12px;
  color: #ffffff;
  font-weight: bold;
  text-transform: uppercase;
  font-size: 20px;
}

.counter-text {
  font-size: 24px;
  margin: 10px 0;
}

button {
  background: linear-gradient(135deg, #E6B99A, #C5A67A);
  color: #333;
  border: none;
  padding: 12px 28px;
  margin-top: 10px;
  cursor: pointer;
  border-radius: 30px;
  transition: background 0.3s, transform 0.2s, box-shadow 0.3s;
  font-size: 18px;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
}

button:hover {
  background: linear-gradient(135deg, #C5A67A, #E6B99A);
  transform: translateY(-4px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
}

.color-box {
  width: 140px;
  height: 140px;
  margin: 20px auto;
  border-radius: 50%;
  border: 5px solid rgba(0, 0, 0, 0.1);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: background-color 0.3s, transform 0.3s;
}

.color-box:hover {
  transform: scale(1.1);
}

.carousel {
  position: relative;
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
}

.carousel img {
  width: 450px;
  height: 450px;
  border-radius: 12px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
}

.carousel-caption {
  margin-top: 15px;
  font-size: 18px;
  color: #6c6c6c;
  font-style: italic;
}

.carousel-controls {
  display: flex;
  justify-content: center;
  margin-top: 15px;
}

.carousel-controls button {
  background: linear-gradient(135deg, #E6B99A, #C5A67A);
  color: #333;
  margin: 0 8px;
  padding: 12px 24px;
  border-radius: 30px;
  border: none;
  cursor: pointer;
  transition: background 0.3s, transform 0.2s;
}

.carousel-controls button:hover {
  background: linear-gradient(135deg, #C5A67A, #E6B99A);
  transform: scale(1.05);
}

footer {
  text-align: center;
  padding: 20px;
  background: #f7f7f7;
  border-top: 1px solid #e0e0e0;
  color: #6c6c6c;
  font-size: 16px;
}
</style>
