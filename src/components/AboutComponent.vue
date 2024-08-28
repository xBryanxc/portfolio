<template>
    <div class="about-container">
      <div class="terminal">
        <div class="terminal-header">
          <div class="header-button red"></div>
          <div class="header-button yellow"></div>
          <div class="header-button green"></div>
        </div>
        <div class="terminal-window">
          <div v-for="(statement, index) in statements" :key="index" class="statement">
            <div class="input-statement">{{ statement.input }}</div>
            <div class="return-statement" v-html="processReturn(statement.return)"></div>
          </div>
          <div class="statement">
            <div class="input-statement">
              <span>&nbsp;</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  import { defineProps } from 'vue';
  
  interface Statement {
    input: string;
    return: string;
  }
  
  const props = defineProps<{
    statements: Statement[]
  }>();
  
  const processReturn = (returnValue: string) => {
    const linkedinRegex = /\blinkedin\b/gi;
  
    let processedValue = returnValue.replace(linkedinRegex, '<a href="https://www.linkedin.com/in/bryan-zuñiga-499070241" target="_blank" rel="noopener noreferrer" class="linkedin-link">LinkedIn</a>');
  
    return processedValue;
  };
  </script>
  
  <style scoped>
.about-container {
  margin: 20vh auto 0;
  width: 100%;
  max-width: 800px; /* Increased from 600px */
  padding: 0 20px; /* Added padding for smaller screens */
}

.terminal {
  width: 100%;
  background-color: #5a5d7a;
  border-radius: 10px;
  overflow: hidden; /* To ensure the rounded corners are visible */
  box-shadow: 0 50px 100px rgba(50, 50, 93, 0.15),
    0 15px 35px rgba(50, 50, 93, 0.2), 0 5px 15px rgba(0, 0, 0, 0.12);
}

.terminal-header {
  height: 28px;
  background-color: #e4e3e5;
  display: flex;
  align-items: center;
  padding-left: 10px;
}

.header-button {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  margin-right: 8px;
}

.red { background-color: #f96256; border: solid 1px #f65549; }
.yellow { background-color: #fdbc3d; border: solid 1px #ffb524; }
.green { background-color: #33c948; border: solid 1px #2dbb41; }

.terminal-window {
  font-family: 'Monaco', Consolas, 'Lucida Console', monospace;
  padding: 20px;
}

.statement {
  margin-bottom: 20px;
}

.input-statement {
  color: #f7f7f7;
}

.input-statement::before {
  content: '> ';
}

.return-statement {
  color: #e7d184;
}

.terminal-window a {
  color: inherit;
  text-decoration: none;
}

.terminal-window .linkedin-link {
  color: #e7d184;
  cursor: pointer;
}

.terminal-window .linkedin-link:hover {
  text-decoration: none;
}

@keyframes caret {
  50% { background-color: transparent; }
}

.input-statement span {
  background: rgba(247, 247, 247, 0.65);
  animation: caret 1s steps(1) infinite;
}

@media (max-width: 600px) {
  .about-container {
    margin-top: 10vh;
  }
}
</style>