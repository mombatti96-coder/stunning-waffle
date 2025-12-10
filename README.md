# stunning-waffle
js_code = """
<script>
  document.addEventListener('DOMContentLoaded', function() {
    const link = document.getElementById('link');
    const popup = document.getElementById('popup');
    const yesBtn = document.getElementById('yes');
    const noBtn = document.getElementById('no');
    const confettiContainer = document.getElementById('confetti-container');

    link.addEventListener('click', function(e) {
      e.preventDefault();
      popup.style.display = 'block';
      // Center the popup initially
      popup.style.left = '50%';
      popup.style.top = '50%';
      popup.style.transform = 'translate(-50%, -50%)';
    });

    noBtn.addEventListener('mouseover', function() {
      const maxX = window.innerWidth - popup.offsetWidth;
      const maxY = window.innerHeight - popup.offsetHeight;

      const newX = Math.random() * maxX;
      const newY = Math.random() * maxY;

      popup.style.left = newX + 'px';
      popup.style.top = newY + 'px';
      popup.style.transform = 'none'; // Remove centering transform
    });

    yesBtn.addEventListener('click', function() {
      popup.style.display = 'none';
      generateConfetti();
    });

    function generateConfetti() {
      confettiContainer.innerHTML = ''; // Clear previous confetti

      for (let i = 0; i < 100; i++) {
        const confetti = document.createElement('div');
        confetti.className = 'confetti';
        confetti.style.left = Math.random() * 100 + 'vw';
        confetti.style.backgroundColor = `hsl(${Math.random() * 360}, 100%, 70%)`;
        confetti.style.animationDelay = Math.random() * 2 + 's';
        confetti.style.animationDuration = (Math.random() * 3 + 2) + 's'; // Random duration between 2-5s
        confetti.style.transform = `rotate(${Math.random() * 360}deg)`;
        confettiContainer.appendChild(confetti);

        // Remove confetti after animation to prevent DOM bloat
        confetti.addEventListener('animationend', () => {
          confetti.remove();
        });
      }
    }
  });
</script>
"""

print("JavaScript code for interactivity has been generated. Please place this code within the `<body>` section of your HTML document, preferably at the end.")
