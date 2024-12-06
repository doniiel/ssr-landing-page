<template>
    <div class="container">
      <h1 class="title">
        Успейте сдать 250 форму вовремя — избегайте штрафов и спите спокойно
      </h1>
      <ul class="details">
        <li>Вы — учредитель / руководитель компании или ИП?</li>
        <li>Ваш портфель состоит из разных активов (ценные бумаги, криптовалюта, имущество за рубежом)?</li>
        <li>Вы не знаете как правильно заполнить декларацию?</li>
      </ul>
      <h2 class="countdown-title">До завершения срока подачи Декларации осталось:</h2>
  
      <div class="countdown">
        <div class="time">
          <span class="number">{{ days }}</span>
          <span class="label">Дни</span>
        </div>
        <div class="time">
          <span class="number">{{ hours }}</span>
          <span class="label">Часы</span>
        </div>
        <div class="time">
          <span class="number">{{ minutes }}</span>
          <span class="label">Минуты</span>
        </div>
        <div class="time">
          <span class="number">{{ seconds }}</span>
          <span class="label">Секунды</span>
        </div>
      </div>
  
      <button class="cta-button">Оставить заявку</button>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  
  // Установите дату для окончания отсчета
  const deadline = new Date('2024-12-31T23:59:59').getTime();
  const days = ref(0);
  const hours = ref(0);
  const minutes = ref(0);
  const seconds = ref(0);
  
  const updateTimer = () => {
    const now = new Date().getTime();
    const timeLeft = deadline - now;
  
    if (timeLeft <= 0) {
      // Если время истекло
      days.value = 0;
      hours.value = 0;
      minutes.value = 0;
      seconds.value = 0;
    } else {
      days.value = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
      hours.value = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      minutes.value = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
      seconds.value = Math.floor((timeLeft % (1000 * 60)) / 1000);
    }
  };
  
  onMounted(() => {
    updateTimer();
    setInterval(updateTimer, 1000);
  });
  </script>
  
  <style>
  body {
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
    background-color: #2f2f2f;
    color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
  }
  
  .container {
    text-align: center;
    padding: 20px;
  }
  
  .title {
    font-size: 2rem;
    font-weight: bold;
    margin-bottom: 20px;
    color: #fff;
  }
  
  .details {
    list-style: none;
    padding: 0;
    margin: 20px 0;
    font-size: 1.2rem;
    line-height: 1.5;
  }
  
  .details li {
    color: #ffb74d;
  }
  
  .countdown-title {
    font-size: 1.5rem;
    font-weight: bold;
    margin-top: 20px;
    color: #fff;
  }
  
  .countdown {
    display: flex;
    justify-content: center;
    gap: 20px;
    margin-bottom: 20px;
  }
  
  .time {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .number {
    font-size: 3rem;
    font-weight: bold;
    color: #fff;
  }
  
  .label {
    font-size: 1rem;
    color: #b0b0b0;
  }
  
  .cta-button {
    padding: 15px 30px;
    background-color: #ff5722;
    color: white;
    font-size: 1.2rem;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  .cta-button:hover {
    background-color: #e64a19;
  }
  </style>
  