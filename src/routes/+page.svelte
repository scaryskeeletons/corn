<style>
    @import './page/page.css';
</style>
  
  <!-- Animation is defined via SVG -->
  <svg viewBox="0 0 100 100" fill="none" class="size-0">
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
  
  <!-- Demo -->
  <header class="header">
      <img src='https://images.unsplash.com/photo-1492931307820-62fa5a68e0df?crop=entropy&cs=srgb&fm=jpg&ixid=M3wzMjM4NDZ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MTU2Njk3MDN8&ixlib=rb-4.0.3&q=85' alt='' class="header-img">
  </header>
  
  <main class="main">
      <h2 class="main-heading">Demo on a simple <code>&lt;div&gt;</code>-Element</h2>
      <div class="demo-div"></div>
  </main>
  