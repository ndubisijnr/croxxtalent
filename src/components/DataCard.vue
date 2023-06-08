<script setup>
import { ref } from 'vue'

defineProps({
  name: String,
  info: String,
  level: String,
  score: String,
  Attempt: String,
})

const count = ref(0)
</script>

<template>

  <div class="data-card">
    <div class="data-card-info">
      <div class="img-profile"></div>
      <div class="data-card-info-inner">
        <span class="info-name">{{name}}</span>
        <span class="info-info"> {{info}}</span>
      </div>
    </div>
    <div class="data-card-info-inner k">
      <span class="info-name">Level</span>
      <span class="badge">{{ level }}</span>
    </div>
    <div class="data-card-info-inner">
      <span class="info-name"> Score</span>
      <span class="info-info">{{ score }}</span>
    </div>
    <div class="data-card-info-inner">
      <span class="info-name">Attempts</span>
      <span class="info-info">{{Attempt}}</span>
    </div>
  </div>


</template>

<style scoped>
.read-the-docs {
  color: #888;
}

.badge{
  border: solid mediumpurple .5px;
  border-radius: 30px;
  padding: 5px;
  font-size: 12px;
  color: mediumpurple;
}

.k{
  width: 80px !important;
}

.data-card-info{
  display: flex;
  align-items: center;
  gap: 10px;
}
.data-card-info-inner{
  display: flex;
  flex-direction: column;
  gap: 5px;
  /*border: solid;*/
  width: auto;
  align-items: start;
}

.info-name{
  font-size: 14px;
  font-weight: 900;
}

.info-info{
  font-size: 12px;
  letter-spacing: .1rem;
  font-weight: 500;
  color: rgba(128, 128, 128, 0.91);
}

.img-profile{
  width: 50px;
  height: 50px;
  border-radius: 360px;
  background-color: #181818;
}

.data-card{
  border: solid .5px;
  width: 95%;
  border-radius:30px;
  display: flex;
  height: 100px;
  align-items: center;
  justify-content: start;
  padding-left: 20px;
  padding-right: 20px;
  gap: 180px;
  margin-bottom: 20px;
}
</style>
