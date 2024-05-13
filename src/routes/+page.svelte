<script>
    import { onMount } from 'svelte';
  
    let animation_length = 5; // Speed at which kernels fall
  
    onMount(() => {
      const container = document.querySelector('#pop_corn_container');
  
      function createPopcorn() {
        var p = document.createElement('div');
        p.className = 'dot';
        // Pick random size between 25-60
        var scale = (Math.random() * 35) + 25;
        p.style.width = `${scale}px`;
        p.style.height = `${scale}px`;
        p.style.left = `${Math.random() * (window.innerWidth - 35)}px`;
        p.style.top = `${Math.random() * (window.innerHeight * 0.5)}px`;
        p.style.animation = `pop ${animation_length}s linear forwards`;
        container.appendChild(p);
  
        // Remove excess kernels
        setTimeout(() => {
          p.remove();
        }, 1000 * animation_length);
      }
  
      // Create a kernel every second
      const intervalId = setInterval(createPopcorn, 1000);
  
      // Clean up the interval when the component is destroyed
      return () => {
        clearInterval(intervalId);
      };
    });
  </script>
  <div class="social-links">
    <a href="https://twitter.com/popcorncatcoin" target="_blank" rel="noopener" class="social-link">
        <img src="https://github.com/scaryskeeletons/images/raw/main/twitter.webp" alt="Twitter"/>
    </a>
    <a href="https://dexscreener.com/solana/5224rcugggwgm7y3ffhrnfz16dk72zmpjx31btv4bcpi" target="_blank" rel="noopener" class="social-link">
        <img src="https://github.com/scaryskeeletons/images/raw/main/dexscreener.webp" alt="Dex Screener"/>
    </a>
    <a href="https://t.me/popcorncatcoin" target="_blank" rel="noopener" class="social-link">
        <img src="https://github.com/scaryskeeletons/images/raw/main/telegram.webp" alt="Telegram"/>
    </a>
</div>

  <iframe width="560" height="315" src="https://www.youtube.com/embed/PnJo7d-xBjY" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"></iframe>
  
  <div id="pop_corn_container"></div>
  
  <style>
    @import './page/page.css';
  </style>
  