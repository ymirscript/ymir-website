<script setup lang="ts">
function onCardsHover(e: MouseEvent) {
  document.querySelectorAll('.card').forEach((card: any) => {
    const rect = card.getBoundingClientRect();
		const x = e.clientX - rect.left;
		const y = e.clientY - rect.top;

		card.style.setProperty("--xPos", `${x}px`);
		card.style.setProperty("--yPos", `${y}px`);
  });
}

function copyCommand(prefix: "unix"|"win") {
  const span = document.getElementById(`${prefix}-command`) as HTMLSpanElement;
  if (span && window.navigator.clipboard) {
    window.navigator.clipboard.writeText(span.innerText).then(() => {
      const btn = span.nextElementSibling as HTMLSpanElement;
      const classes = btn.className;
      btn.innerText = "Copied!";
      btn.className = "";
      setTimeout(() => {
        btn.innerText = "";
        btn.className = classes;
      }, 1000);
    });
  }
}

</script>

<template>
  <div class="wrapper">
    <nav class="site-nav">
      <a class="navitem" href="#home">
        Home
      </a>
      <a class="navitem" href="#features">
        Features
      </a>
      <a class="navitem" href="#install">
        Installation
      </a>
      <a class="navitem" href="#more">
        More
      </a>
    </nav>

    <div class="top-container" id="home">
      <div class="introduction">
        <h2><span class="highlight">Ymir</span>: Unleash the power of adaptive <span class="highlight">code generation</span> for <span class="highlight">modern web development</span></h2>
        <p>Simplify more. Adapt faster. Expand easier.</p>
        <small>With an intuitive definition language, YmirScript, effortlessly create and manage REST APIs for any target language. Ymir's modular architecture allows seamless integration of target plugins for added flexibility. Experience the power of Code Adaptation, updating boilerplate code without affecting production code, preserving project progress. Harness the efficiency of Ymir, the next generation adaptive compiler for web developers.</small>
      </div>
      <div class="logo">
        <img src="/ymiricon.png"/>
      </div>
    </div>

    <div class="features-container" id="features">
      <div class="title">Features</div>

      <div class="cards" @mouseover="onCardsHover($event)">
        <div class="card">
          <div class="card-content">
            <div class="icon"><i class="fa-solid fa-file-pen"></i></div>
            <p>YmirScript</p>
            <small>Define REST APIs with ease using a simple, intuitive language tailored for web developers. YmirScript allows you to describe your APIs concisely, making it a breeze to maintain and update as your project evolves.</small>
          </div>
        </div>
        <div class="card">
          <div class="card-content">
            <div class="icon"><i class="fa-solid fa-gears"></i></div>
            <p>Code Generation</p>
            <small>Automatically generate boilerplate code in your target language, saving you valuable time and effort. With Ymir, you can focus on your core application logic while the compiler takes care of the repetitive, time-consuming tasks.</small>
          </div>
        </div>
        <div class="card">
          <div class="card-content">
            <div class="icon"><i class="fa-solid fa-bullseye"></i></div>
            <p>Target Plugins</p>
            <small>Enhance Ymir's capabilities by adding support for new languages through plugins. Its extensible nature allows you to customize and expand the compiler to fit your unique requirements, making it the perfect companion for your diverse projects.</small>
          </div>
        </div>
        <div class="card">
          <div class="card-content">
            <div class="icon"><i class="fa-solid fa-wand-magic-sparkles"></i></div>
            <p>Code Adaptation</p>
            <small>Safeguard your project progress with Ymir's Code Adaptation feature. Update boilerplate code without affecting production code, ensuring that any modifications in the development process do not hinder your project's advancement.</small>
          </div>
        </div>
        <div class="card">
          <div class="card-content">
            <div class="icon"><i class="fa-solid fa-cubes"></i></div>
            <p>Modular Architecture</p>
            <small>Ymir's modular architecture empowers you to customize and expand its functionality to suit your project's needs. This adaptable design makes Ymir an invaluable asset in various development scenarios.</small>
          </div>
        </div>
        <div class="card">
          <div class="card-content">
            <div class="icon"><i class="fa-solid fa-puzzle-piece"></i></div>
            <p>Easy Integration</p>
            <small>Incorporate Ymir seamlessly into your development workflow for optimal efficiency. Its user-friendly nature allows you to integrate it effortlessly into your existing processes, enabling you to work smarter and faster.</small>
          </div>
        </div>
      </div>
    </div>

    <div class="install-container" id="install">
      <div class="title">Installation</div>

      <div class="setups">
        <div class="setup">
          <div class="title">
            <i class="fa-brands fa-windows"></i>
            <span>Windows</span>
          </div>

          <div class="command">
            <span class="text" id="win-command">irm https://ymirscript.dev/install/setup-windows.ps1 | iex</span>
            <i class="btn fa-solid fa-copy" @click="copyCommand('win')"></i>
          </div>
        </div>

        <div class="setup">
          <div class="title">
            <i class="fa-brands fa-linux"></i>
            <span>Linux</span>
          
            <span style="opacity: 0.3; font-size: 1.2rem;">&</span>

            <i class="fa-brands fa-apple"></i>
            <span>MacOS</span>
          </div>

          <div class="command">
            <span class="text" id="unix-command">curl -fsSL https://ymirscript.dev/install/setup-unix.sh | sh</span>
            <i class="btn fa-solid fa-copy" @click="copyCommand('unix')"></i>
          </div>
        </div>
      </div>
    </div>

    <div class="more-container" id="more">
      <div class="title">
        Ready to revolutionize your web development workflow?
      </div>
      <div class="subtitle">
        Interested in exploring Ymir's full potential? Dive into our comprehensive documentation, discover the source code on GitHub, and show your support by starring our repository!
      </div>

      <div class="links">
        <a class="link" href="https://github.com/ymirscript/ymir/wiki">
          <i class="fa-solid fa-book"></i>
          <p>Explore the Docs</p>
        </a>
        
        <a class="link" href="https://github.com/ymirscript">
          <i class="fa-brands fa-github"></i>
          <p>View on GitHub</p>
        </a>
        
        <a class="link" href="https://github.com/ymirscript/ymir">
          <i class="fa-solid fa-star"></i>
          <p>Star the Repository</p>
        </a>
      </div>
    </div>
  </div>
</template>