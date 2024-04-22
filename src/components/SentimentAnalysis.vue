<template>
    <div>
      <h1>Sentiment Analysis</h1>
      <textarea v-model="inputText" placeholder="Enter text for sentiment analysis"></textarea>
      <button @click="analyzeSentiment">Analyze</button>
      <div v-if="sentimentResult" class="result">
        <h2>Analysis Result:</h2>
        <p>Sentiment: {{ sentimentResult.sentiment }}</p>
        <p>Confidence: {{ sentimentResult.confidence }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        inputText: '',
        sentimentResult: null
      };
    },
    methods: {
      analyzeSentiment() {
        // You can perform sentiment analysis here using an API or library
        // For simplicity, let's assume sentiment analysis is done locally
        // Replace this with actual sentiment analysis logic
        const sentiment = Math.random() < 0.5 ? 'Positive' : 'Negative';
        const confidence = Math.floor(Math.random() * 100) + 1;
        this.sentimentResult = { sentiment, confidence };
      }
    }
  };
  </script>
  
  <style scoped>
  /* Style for textarea */
  textarea {
    width: 100%;
    height: 100px;
    margin-bottom: 10px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 16px;
  }
  
  /* Style for analyze button */
  button {
    padding: 10px 20px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
    transition: background-color 0.3s ease;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  
  /* Style for result container */
  .result {
    margin-top: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 20px;
    background-color: #f9f9f9;
  }
  
  /* Style for sentiment text */
  .sentiment-text {
    font-size: 20px;
    font-weight: bold;
    margin-bottom: 10px;
  }
  
  /* Style for confidence text */
  .confidence-text {
    font-size: 18px;
  }
  
  /* Media query for smaller screens */
  @media (max-width: 768px) {
    textarea {
      height: 80px;
    }
  }
  </style>
  