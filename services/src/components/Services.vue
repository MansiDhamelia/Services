<template>
  <div class="main">
    <div class="mainContainer">
      <h1>Services</h1>
      <div class="container">
        <div
          class="item1"
          @click="get(index)"
          v-for="(service, index) in services"
          :key="index"
          :style="isActive(index)"
        >
          <p>{{ service.name }}</p>
          <p id="price1">${{ service.price }}.00</p>
        </div>
        <div class="item2" id="totalId">
          <p>Total:</p>
          <p id="totalAmount">${{ result || 0.0 }}.00</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      services: [
        {
          name: "Web Development",
          price: 300,
          isActive: false,
        },
        {
          name: "Design",
          price: 400,
          isActive: false,
        },
        {
          name: "Integration",
          price: 250,
          isActive: false,
        },
        {
          name: "Training",
          price: 220,
          isActive: false,
        },
      ],
    };
  },

  computed: {
    result() {
      let total = 0;
      this.services.filter((e) => {
        if (e.isActive) {
          total += e.price;
          console.log(total);
        }
      });
      return total;
    },
  },
  methods: {
    get(index) {
      (this.services[index].isActive = !this.services[index].isActive),
        console.log(this.isActive);
    },
    isActive(index) {
      return {
        backgroundColor: this.services[index].isActive ? "green" : "pink",
      };
    },
  },
};
</script>

<style scoped>
.main {
  display: flex;
  min-height: 100vh;
  justify-content: center;
  align-items: center;
  background-color: whitesmoke;
}
.mainContainer {
  width: 500px;
  height: 520px;
  display: flex;
  justify-content: start;
  align-items: center;
  background-color: #3985a8;
  flex-direction: column;
  border-radius: 3px;
}
h1 {
  font-family: "Brush Script MT", cursive;
  font-size: 60px;
  color: white;
}
p {
  font-weight: bold;
  color: white;
}
.container {
  height: 350px;
  width: 350px;
  margin: 10px;
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  align-items: center;
}
.item1 {
  display: flex;
  font-size: 20px;
  width: 100%;
  align-items: flex-start;
  justify-content: space-between;
  padding: 0px 25px 0px 25px;
  border-bottom: 1px black;
}

.item1:hover {
  cursor: pointer;
}

.item2 {
  display: flex;
  font-size: 20px;
  width: 100%;
  align-items: flex-start;
  justify-content: space-between;
  padding: 0px 25px 0px 25px;
}

#totalId {
  border-top: black 2px;
}
</style>
