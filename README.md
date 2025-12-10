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

from IPython.display import HTML

html_content = f"""
<style>
  body {{ font-family: sans-serif; display: flex; justify-content: center; align-items: center; min-height: 100vh; margin: 0; background-color: #f0f0f0; overflow: hidden; }}
  #link {{ padding: 10px 20px; background-color: #007bff; color: white; border-radius: 5px; text-decoration: none; cursor: pointer; position: relative; z-index: 10; }}
  #popup {{ display: none; position: fixed; background-color: white; border: 2px solid #ccc; border-radius: 8px; padding: 20px; box-shadow: 0 4px 8px rgba(0,0,0,0.2); z-index: 1000; transition: all 0.5s ease-out; }}
  #popup h2 {{ margin-top: 0; color: #333; }}
  #popup-buttons {{ display: flex; justify-content: space-around; margin-top: 20px; }}
  #popup-buttons button {{ padding: 10px 20px; border: none; border-radius: 5px; cursor: pointer; font-size: 16px; }}
  #yes {{ background-color: #28a745; color: white; }}
  #no {{ background-color: #dc3545; color: white; }}
  .confetti-container {{ position: fixed; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; overflow: hidden; z-index: 999; }}
  .confetti {{ position: absolute; width: 10px; height: 10px; border-radius: 50%; animation: fall 3s forwards ease-out; opacity: 0; }}

  @keyframes fall {{
    0% {{ transform: translateY(-100vh) rotate(0deg); opacity: 0; }}
    10% {{ opacity: 1; }}
    100% {{ transform: translateY(100vh) rotate(720deg); opacity: 0; }}
  }}
</style>

<body>
  <a href="#" id="link">Click me!</a>

  <div id="popup">
    <h2>Do you love me?</h2>
    <div id="popup-buttons">
      <button id="yes">Yes</button>
      <button id="no">No</button>
    </div>
  </div>

  <div id="confetti-container"></div>

  {js_code}
</body>
"""

display(HTML(html_content))
