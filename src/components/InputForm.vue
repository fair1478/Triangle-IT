<template>
  <div>
    <form @submit.prevent="submitForm" class="form">
      <label for="side1">Side 1:</label>
      <input
        type="number"
        id="side1"
        v-model="side1"
        required
        min="1"
        max="9999"
      />

      <label for="side2">Side 2:</label>
      <input
        type="number"
        id="side2"
        v-model="side2"
        required
        min="1"
        max="9999"
      />

      <label for="side3">Side 3:</label>
      <input
        type="number"
        id="side3"
        v-model="side3"
        required
        min="1"
        max="9999"
      />

      <button type="submit">Submit</button>
    </form>

    <div v-if="triangleType" class="result">
      <p>{{ triangleType }}</p>
    </div>
  </div>
</template>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 300px;
  margin: 0 auto;
}
label {
  font-weight: 500;
}
input {
  padding: 0.5rem;
  border-radius: 0.25rem;
  border: 1px solid #ccc;
}
button {
  padding: 0.5rem 1rem;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 0.25rem;
  cursor: pointer;
}
.result {
  margin-top: 1rem;
  padding: 0.5rem;
  border-radius: 0.25rem;
  border: 1px solid #ccc;
  text-align: center;
}
.result p {
  margin: 0;
  font-weight: bold;
  color: #4caf50;
}
</style>

<script>
export default {
  data() {
    return {
      side1: null,
      side2: null,
      side3: null,
      triangleType: null,
    };
  },
  methods: {
    submitForm() {
      if (
        this.side1 > 0 &&
        this.side1 <= 9999 &&
        this.side2 > 0 &&
        this.side2 <= 9999 &&
        this.side3 > 0 &&
        this.side3 <= 9999
      ) {
        console.log("Form submitted successfully");
        if (
          this.side1 + this.side2 > this.side3 ||
          this.side1 + this.side3 > this.side2 ||
          this.side2 + this.side3 > this.side1
          // this check is wrong but we follow the design
        ) {
          this.triangleType = this.checkTriangleType();
        }
      } else {
        console.log("Invalid form values");
      }
    },
    checkTriangleType() {
      if (
        this.side1 !== this.side2 &&
        this.side2 !== this.side3 &&
        this.side1 !== this.side3
      ) {
        return "สามเหลี่ยมด้านไม่เท่า (Scalene Triangle)";
      } else if (
        this.side1 === this.side2 &&
        this.side2 === this.side3 &&
        this.side1 === this.side3
      ) {
        return "สามเหลี่ยมด้านเท่า (Equilateral Triangle)";
      } else if (
        this.side1 === this.side2 ||
        this.side2 === this.side3 ||
        // side1 = side2 is wrong but we follow the design
        this.side1 === this.side2
      ) {
        return "สามเหลี่ยมหน้าจั่ว (Isosceles Triangle)";
      } else {
        return "สามเหลี่ยมมุมฉาก (Right Triangle)";
      }
    },
  },
};
</script>
