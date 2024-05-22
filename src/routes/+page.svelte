<script>
    import { onMount } from 'svelte';
    import { scrollTo, scrollRef, scrollTop } from 'svelte-scrolling'

    let animation_length = 4; // Speed at which bubbles rise
    const anchors = Array(100).fill(0).map((_, index) => index)

    // @ts-ignore
    function scrollIntoView({ target }) {
		const el = document.querySelector(target.getAttribute('href'));
		if (!el) return;
    el.scrollIntoView({
      behavior: 'smooth'
    });
  }

    onMount(() => {
      const container = document.querySelector('#bubble_container');
      
      function createBubble() {
        var b = document.createElement('div');
        b.className = 'bubble';
        var scale = (Math.random() * 35) + 25;
        b.style.width = `${scale}px`;
        b.style.height = `${scale}px`;
        b.style.left = `${Math.random() * (window.innerWidth - 35)}px`;
        b.style.bottom = '0px'; // Start from the bottom of the screen
        b.style.animation = `bubbles ${animation_length}s linear forwards`;
        container?.appendChild(b);
  
        setTimeout(() => {
          b.remove();
        }, 1000 * animation_length);
      }
  
      const intervalId = setInterval(createBubble, 400);
  
      return () => {
        clearInterval(intervalId);
      };
    });
  </script>

<div id="bubble_container">
    <div class="section" id="main">
        <nav class="navbar">
            <div class="nav-container">
                <a href="#" class="nav-logo">Snooty</a>
                <ul class="nav-menu">
                    <li class="nav-item"><span class="nav-link" use:scrollTo={{ ref: 'story', duration: 1000 }}><strong>Story</strong></span></li>
                    <li class="nav-item"><span class="nav-link" use:scrollTo={{ ref: 'tokenomics', duration: 1000 }}><strong>Tokenomics</strong></span></li>
                    <li class="nav-item"><span class="nav-link" use:scrollTo={{ ref: 'roadmap', duration: 1000 }}><strong>Roadmap</strong></span></li>
                </ul>
            </div>
        </nav>

        <div>
            <img class="snooty" src="snootyunscaled.png" alt="Snooty"/>
        </div>
    </div>
    <svg viewBox="10 10 10 10" fill="none" class="size-0">
        <defs>
            <filter id="filter">
                <feTurbulence id="turbulence-filter" type="fractalNoise" baseFrequency=".03" numOctaves="1" result="noise" />
                <feDisplacementMap in="SourceGraphic" in2="noise" scale="20" xChannelSelector="B" yChannelSelector="G" />
            </filter>
    
            <animate
                id="anim1"
                xlink:href="#turbulence-filter"
                attributeName="baseFrequency"
                from=".03"
                to=".033"
                dur="3s"
                begin="0s; anim2.end"
                fill="freeze" />
            <animate
                id="anim2"
                xlink:href="#turbulence-filter"
                attributeName="baseFrequency"
                from=".033"
                to=".03"
                dur="3s"
                begin="anim1.end"
                fill="freeze" />
        </defs>
    </svg>
    <section use:scrollRef={'story'}>
        <div class="section" id="story">
            <h1>Snooty's life</h1>
            <p>Snooty had a long and wonderful life living to the age of 69, tragically while following some of the younger manatees Snooty's fat ass got stuck </p>
        </div>
    </section>

    <section use:scrollRef={'tokenomics'}>
        <div class="section" id="tokenomics">
            <h1>Tokenomics</h1>
        </div>
    </section>

    <section use:scrollRef={'roadmap'}>
        <div class="section" id="roadmap">
            <h1>Roadmap</h1>
        </div>
    </section>

    <main>
    <div class="overlay"></div>
    </main>
</div>

<style>
    @import 'page/page.css';
</style>