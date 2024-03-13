<script setup>
import { ref } from 'vue'

const items = ref([
  {
    title: 'What is HTML?',
    content:
      'HTML stands for Hyper Text Markup Language. HTML is the standard markup language for creating Web pages.',
    open: false
  },
  {
    title: 'What is CSS?',
    content:
      'CSS is the acronym of “Cascading Style Sheets”. CSS is a computer language for laying out and structuring web pages (HTML or XML)',
    open: false
  },
  {
    title: 'What is JavaScript?',
    content:
      'JavaScript (JS) is a cross-platform, object-oriented programming language used by developers to make web pages interactive.',
    open: false
  }
])

const toggleAccordion = (index) => {
  items.value = items.value.map((item, i) => ({
    ...item,
    open: i === index ? !item.open : false
  }))
}
</script>

<template>
  <div class="accordion-container">
    <div v-for="(item, index) in items" :key="index" class="accordion">
      <div class="accordion-header" @click="toggleAccordion(index)">
        {{ item.title }} <span class="arrow-icon">{{ item.open ? '🔽' : '▶️' }}</span>
      </div>

      <div v-show="item.open" class="accordion-content">{{ item.content }}</div>
    </div>
  </div>
</template>

<style scoped>
.accordion-container {
  max-width: 600px;
  margin: 50px auto;
}

.accordion {
  border: 1px solid #ddd;
  border-radius: 4px;
  overflow: hidden;
  margin-bottom: 10px;
}

.accordion-header {
  background-color: #3498db;
  color: #fff;
  padding: 15px;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.arrow-icon {
  font-size: 20px;
}

.accordion-content {
  padding: 15px;
  display: none;
  border-top: 1px solid #ddd;
  background-color: #f9f9f9;
  color: #333;
}

.accordion-content[style] {
  display: block;
}
</style>
