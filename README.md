
    <!-- ===== BOTTOM NAV ===== -->
    <nav class="bottom-nav">
        <a href="about.html" class="nav-item">
            <i class="fas fa-user nav-icon"></i>
            <span class="nav-label">About</span>
        </a>
        <a href="work.html" class="nav-item">
            <i class="fas fa-book-open nav-icon"></i>
            <span class="nav-label">Works</span>
        </a>
        <a href="skills.html" class="nav-item">
            <i class="fas fa-folder-open nav-icon"></i>
            <span class="nav-label">skills</span>
        </a>
        <a href="reflection.html" class="nav-item">
            <i class="fas fa-lightbulb nav-icon"></i>
            <span class="nav-label">Reflection</span>
        </a>
        <a href="contact.html" class="nav-item">
            <i class="fas fa-paper-plane nav-icon"></i>
            <span class="nav-label">Contact</span>
        </a>
    </nav>

    <!-- ===== JAVASCRIPT ===== -->
    <script>
        // ===== PARTICLE GENERATION =====
        function createParticles() {
            const container = document.getElementById('particles');
            const particleCount = 40;
            for (let i = 0; i < particleCount; i++) {
                const p = document.createElement('div');
                p.classList.add('particle');
                p.style.left = Math.random() * 100 + '%';
                p.style.animationDelay = Math.random() * 15 + 's';
                p.style.animationDuration = (10 + Math.random() * 10) + 's';
                container.appendChild(p);
            }
        }

        // ===== SCROLL PROGRESS =====
        function updateProgressBar() {
            const scrollTop = window.scrollY;
            const docHeight = document.documentElement.scrollHeight - window.innerHeight;
            const progress = (scrollTop / docHeight) * 100;
            document.getElementById('progressBar').style.width = progress + '%';
        }

        // ===== TYPING EFFECT =====
        const phrases = [
            'Creating • Learning • Growing',
            'Welcome to my portfolio ✨',
            'Explore my works 📖',
            'Dream big, learn more 🚀'
        ];
        let phraseIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        const typingSpeed = 100;
        const deletingSpeed = 50;
        const pauseTime = 2000;

        function typeEffect() {
            const currentPhrase = phrases[phraseIndex];
            const el = document.getElementById('typing');
            
            if (isDeleting) {
                el.textContent = currentPhrase.substring(0, charIndex - 1);
                charIndex--;
            } else {
                el.textContent = currentPhrase.substring(0, charIndex + 1);
                charIndex++;
            }

            let speed = isDeleting ? deletingSpeed : typingSpeed;

            if (!isDeleting && charIndex === currentPhrase.length) {
                speed = pauseTime;
                isDeleting = true;
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                phraseIndex = (phraseIndex + 1) % phrases.length;
                speed = 500;
            }

            setTimeout(typeEffect, speed);
        }

        // ===== INITIALIZE =====
        document.addEventListener('DOMContentLoaded', function() {
            createParticles();
            typeEffect();
            window.addEventListener('scroll', updateProgressBar);
        });
    </script>
    
</body>
</html>

