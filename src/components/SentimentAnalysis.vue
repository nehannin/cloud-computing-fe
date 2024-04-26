<template>
    <div>
      <h1>Sentiment Analysis</h1>
      <textarea v-model="inputText" placeholder="Enter text for sentiment analysis"></textarea>
      <button @click="analyzeSentiment">Analyze</button>
      <div v-if="sentimentResult" class="result">
        <h2>Analysis Result:</h2>
        <p class="sentiment-text">Sentiment: {{ sentimentResult.sentiment }}</p>
        <p class="confidence-text">Confidence: {{ sentimentResult.confidence }}</p>
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
      async analyzeSentiment() {
        try {
            const response = await fetch('http://localhost:8080/analyze_sentiment', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({ text: this.inputText }),
            });

            if (!response.ok) {
                throw new Error('Failed to analyze sentiment');
            }

            const data = await response.json();
            this.sentimentResult = data;
        } catch (error) {
            console.error(error);
            this.sentimentResult = null;
        }
    }

    }
  };
  </script>
  
  <style scoped>
  textarea {
    width: 100%;
    height: 100px;
    margin-top: 10px;
    margin-bottom: 10px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 1rem;
  }
  
  button {
    padding: 10px 20px;
    margin-top: 10px;
    margin-bottom: 10px;
    width: 100%;
    background-color: #828a41;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 1rem;
    transition: background-color 0.3s ease;
  }
  
  button:hover {
    background-color: #444924;
  }
  
  .result {
    margin-top: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 20px;
  }
  
  .sentiment-text {
    font-size: 1.25rem;
    font-weight: bold;
    margin-bottom: 10px;
  }
  
  .confidence-text {
    font-size: 1.125rem;
  }
  
  @media (max-width: 768px) {
    textarea {
      height: 80px;
    }
  }
  </style>
  