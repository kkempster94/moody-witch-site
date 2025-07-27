<script lang="ts">
  import { onMount } from 'svelte';
  
  let mounted = false;
  
  onMount(() => {
    mounted = true;
  });
</script>

<main class:mounted>
  <div class="container">
    <h1 class="title">Moody Witch Art</h1>
    <p class="subtitle">Coming Soon</p>
    <div class="glow-effect"></div>
  </div>
</main>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    font-family: 'Arial', sans-serif;
    background: linear-gradient(45deg, #1a0033, #330066, #4d0080);
    background-size: 400% 400%;
    animation: gradientShift 8s ease infinite;
    overflow: hidden;
  }

  @keyframes gradientShift {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }

  main {
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    opacity: 0;
    transform: translateY(20px);
    transition: all 1s ease-out;
  }

  main.mounted {
    opacity: 1;
    transform: translateY(0);
  }

  .container {
    text-align: center;
    position: relative;
    z-index: 2;
  }

  .title {
    font-size: clamp(3rem, 8vw, 8rem);
    font-weight: bold;
    margin: 0;
    background: linear-gradient(45deg, #ff00ff, #8000ff, #ff0080, #ff00ff);
    background-size: 200% 200%;
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: neonPulse 3s ease-in-out infinite, textGlow 2s ease-in-out infinite alternate;
    text-shadow: 0 0 20px rgba(255, 0, 255, 0.5);
  }

  @keyframes neonPulse {
    0%, 100% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
  }

  @keyframes textGlow {
    from { 
      filter: drop-shadow(0 0 10px rgba(255, 0, 255, 0.8));
    }
    to { 
      filter: drop-shadow(0 0 30px rgba(255, 0, 255, 1));
    }
  }

  .subtitle {
    font-size: clamp(1.5rem, 4vw, 3rem);
    color: #ff80ff;
    margin: 1rem 0;
    text-shadow: 0 0 15px rgba(255, 128, 255, 0.8);
    animation: subtitleGlow 2.5s ease-in-out infinite alternate;
  }

  @keyframes subtitleGlow {
    from { 
      text-shadow: 0 0 15px rgba(255, 128, 255, 0.8);
    }
    to { 
      text-shadow: 0 0 25px rgba(255, 128, 255, 1);
    }
  }

  .glow-effect {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 200px;
    height: 200px;
    background: radial-gradient(circle, rgba(255, 0, 255, 0.3) 0%, transparent 70%);
    border-radius: 50%;
    animation: pulse 4s ease-in-out infinite;
    z-index: -1;
  }

  @keyframes pulse {
    0%, 100% {
      transform: translate(-50%, -50%) scale(1);
      opacity: 0.3;
    }
    50% {
      transform: translate(-50%, -50%) scale(1.5);
      opacity: 0.6;
    }
  }
</style>