//html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Janvi- Portfolio</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <div class="container">
            <!-- Your name or logo -->
            <h1>Janvi</h1>
            <div class="menu-toggle">
                <span></span>
                <span></span>
                <span></span>
            </div>
            <!-- Navigation menu -->
            <nav>
                <ul>
                    <li><a href="#about">About</a></li>
                    <li><a href="#projects">Projects</a></li>
                    <li><a href="#resume">Resume</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <main>
        <section id="about">
            "Crafting intuitive experiences with code and creativity."
        </section>

        <section id="projects">
Conversational Chatbot for Institutions
• The conversational chatbot for institutes, named ”Pluto,” served as an automated assistant to streamline various
educational processes. It accepted both text and voice-based queries from students, faculty, and staff, providing
relevant information and assistance.
Pet Guard:Pet Helpline
• The Pet Care WebApp is a user-friendly online platform designed to enhance the well-being of all pet animals through
essential assistance and support.
PHP Project: TO DO LIST
• The To-Do List application was designed to help users manage their tasks.
        </section>

        <section id="contact">
            Pune, Maharastra | motwanijanvi68@gmail.com |
            <div class="container">
                <h2>Contact Me</h2>
                <form>
                    <input type="text" name="name" placeholder="Your Name">
                    <input type="email" name="email" placeholder="Your Email">
                    <textarea name="message" placeholder="Your Message"></textarea>
                    <button type="submit">Send Message</button>
                </form>
            </div>
        </section>
    </main>

    <footer>
        <div class="container">
            <!-- Add footer content here -->
        </div>
    </footer>

    <!-- Add JavaScript files here if you need interactivity -->
    <script src="script.js"></script>
</body>
</html>
//CSS
body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    margin: 0;
    padding: 0;
}

.container {
    width: 80%;
    max-width: 1200px;
    margin: 0 auto;
}

header {
    background-color: #333;
    color: #fff;
    padding: 20px 0;
}

header h1 {
    margin: 0;
    float: left;
}

.menu-toggle {
    display: none;
    float: right;
    cursor: pointer;
}

.menu-toggle span {
    display: block;
    width: 25px;
    height: 3px;
    background-color: #fff;
    margin-bottom: 5px;
}

nav {
    float: right;
}

nav ul {
    list-style: none;
    padding: 0;
    margin: 0;
}

nav ul li {
    display: inline-block;
    margin-left: 20px;
}

nav ul li a {
    color: #fff;
    text-decoration: none;
    transition: color 0.3s ease;
}

nav ul li a:hover {
    color: #ccc;
}

main {
    padding: 20px 0;
}

section {
    padding: 20px 0;
}

footer {
    background-color: #333;
    color: #fff;
    padding: 20px 0;
    text-align: center;
}

#contact {
    background-color: #f9f9f9;
}

#contact form {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    background-color: #fff;
}

#contact form input[type="text"],
#contact form input[type="email"],
#contact form textarea {
    width: 100%;
    margin-bottom: 20px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

#contact form button {
    width: 100%;
    padding: 10px;
    background-color: #333;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

#contact form button:hover {
    background-color: #555;
}

/* Responsive Styles */
@media (max-width: 768px) {
    .container {
        width: 90%;
    }

    header {
        padding: 10px 0;
    }

    header h1 {
        float: none;
        text-align: center;
    }

    .menu-toggle {
        display: block;
    }

    nav {
        display: none;
        clear: both;
    }

    nav.active {
        display: block;
    }

    nav ul {
        text-align: center;
    }

    nav ul li {
        display: block;
        margin: 10px 0;
    }
}

//JS

document.addEventListener('DOMContentLoaded', () => {
    
    const navLinks = document.querySelectorAll('header a');

    navLinks.forEach(link => {
        link.addEventListener('click', (e) => {
            e.preventDefault();
            const targetSection = document.querySelector(link.getAttribute('href'));
            targetSection.scrollIntoView({ behavior: 'smooth' });
        });
    });

    
    const sections = document.querySelectorAll('section');

    window.addEventListener('scroll', () => {
        let current = '';
        sections.forEach(section => {
            const sectionTop = section.offsetTop;
            const sectionHeight = section.clientHeight;
            if (pageYOffset >= (sectionTop - sectionHeight / 3)) {
                current = section.getAttribute('id');
            }
        });
        navLinks.forEach(link => {
            link.classList.remove('active');
            if (link.getAttribute('href').substring(1) === current) {
                link.classList.add('active');
            }
        });
    });

    // Responsive navigation menu for mobile devices
    const menuToggle = document.querySelector('.menu-toggle');
    const navigation = document.querySelector('header nav');

    menuToggle.addEventListener('click', () => {
        navigation.classList.toggle('active');
    });

    // Form validation for the contact section
    const contactForm = document.querySelector('#contact form');

    contactForm.addEventListener('submit', (e) => {
        e.preventDefault();
        const nameInput = document.querySelector('#contact input[name="name"]');
        const emailInput = document.querySelector('#contact input[name="email"]');
        const messageInput = document.querySelector('#contact textarea[name="message"]');
        const name = nameInput.value.trim();
        const email = emailInput.value.trim();
        const message = messageInput.value.trim();

        if (name === '' || email === '' || message === '') {
            alert('Please fill in all fields.');
        } else if (!isValidEmail(email)) {
            alert('Please enter a valid email address.');
        } else {
            // Here you can implement form submission logic (e.g., using AJAX)
            alert('Form submitted successfully!');
            // Clear form fields after submission
            nameInput.value = '';
            emailInput.value = '';
            messageInput.value = '';
        }
    });

    function isValidEmail(email) {
        // Basic email validation
        const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return regex.test(email);
    }

    // Smooth scroll-to-top button
    const scrollToTopButton = document.querySelector('.scroll-to-top');

    window.addEventListener('scroll', () => {
        if (window.scrollY > 500) {
            scrollToTopButton.classList.add('show');
        } else {
            scrollToTopButton.classList.remove('show');
        }
    });

    scrollToTopButton.addEventListener('click', () => {
        window.scrollTo({ top: 0, behavior: 'smooth' });
    });
});


