---
title: "Contact"
permalink: /contact/
layout: single
---

<div class="contact-section">
  <div class="contact-details">
    <h2>Contact Details</h2>
    <ul>
      <li><strong>Email:</strong> <a href="mailto:gterfa@ucsd.edu">gterfa@ucsd.edu</a></li>
      <li><strong>LinkedIn:</strong> <a href="https://linkedin.com/in/girma-terfa-cs" target="_blank">LinkedIn Profile</a></li>
      <li><strong>GitHub:</strong> <a href="https://github.com/gir-ma" target="_blank">GitHub Page</a></li>
      <li><strong>Personal Email:</strong> <a href="mailto:girma4w@gmail.com">girma4w@gmail.com</a></li>
      <li><strong>Current Location:</strong> San Diego, CA</li>
    </ul>
    <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3381.552469031871!2d-117.2359142846117!3d32.88006008094002!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x80dbff8e4a2b48a7%3A0xb0e6c87e57774b63!2sUniversity%20of%20California%20San%20Diego!5e0!3m2!1sen!2sus!4v1636207076747!5m2!1sen!2sus" width="300" height="200" style="border:0;" allowfullscreen="" loading="lazy"></iframe>
  </div>
  
<div class="contact-form" id="contact-form">
  <h2>Contact Me</h2>
  <form id="contactForm">
    <label for="name">Name:</label><br>
    <input type="text" id="name" name="name" required><br>
    
    <label for="email">Email:</label><br>
    <input type="email" id="email" name="_replyto" required><br>
    
    <label for="subject">Subject:</label><br>
    <input type="text" id="subject" name="subject" required><br>
    
    <label for="message">Message:</label><br>
    <textarea id="message" name="message" rows="4" required></textarea><br>

    <!-- Honeypot field (hidden from users) -->
    <input type="text" id="website" name="website" style="display:none;">
    
    <input type="submit" value="Send">
  </form>
</div>

<script>
  const form = document.getElementById('contactForm');
  const contactFormDiv = document.getElementById('contact-form');


  // Record load time
  let formLoadTime = Date.now();

  function generateMessageID() {
    // Example: MSG-20250922-abc123
    const datePart = new Date().toISOString().slice(0,10).replace(/-/g,"");
    const randomPart = Math.random().toString(36).substring(2, 8).toUpperCase();
    return `MSG-${datePart}-${randomPart}`;
  }

  form.addEventListener('submit', async function (e) {
    e.preventDefault();

    // Honeypot check
    const honeypot = form.querySelector('#website').value;
    if (honeypot) {
      console.log("Bot detected 🚫");
      return; // silently block bots
    }

    // Time-delay check (minimum 3 seconds)
    const timeTaken = (Date.now() - formLoadTime) / 1000; // in seconds
    if (timeTaken < 3) {
      console.log("🚫 Bot detected via fast submission");
      return;
    }

    // Manual validation extra safety feature
    const name = form.querySelector('#name').value.trim();
    const email = form.querySelector('#email').value.trim();
    const subject = form.querySelector('#subject').value.trim();
    const message = form.querySelector('#message').value.trim();

    if (!name || !email || !subject || !message) {
      alert("Please fill in all fields.");
      return; // stop submission
    }

    // Extra email validation with regex
    const emailPattern = /^[^@\s]+@[^@\s]+\.[^@\s]+$/;
    if (!emailPattern.test(email)) {
      alert("Please enter a valid email address.");
      return;
    }

    const formData = new FormData(form);
    const messageID = generateMessageID(); // generate ID

    // Add the ID into the form data so it’s also sent to Formspree
    formData.append("message_id", messageID);

    try {
      const response = await fetch("https://formspree.io/f/xgvneevn", {
        method: "POST",
        body: formData,
        headers: { 'Accept': 'application/json' }
      });

      if (response.ok) {
        contactFormDiv.innerHTML = `
          <div class="thank-you">
            <h2>Thank you!</h2>
            <p>Your message has been sent successfully.</p>
            <p><strong>Your Message ID:</strong> ${messageID}</p>
          </div>
        `;
      } else {
        contactFormDiv.innerHTML = "<h2>Oops!</h2><p>There was a problem sending your message. Please try again later.</p>";
      }
    } catch (error) {
      contactFormDiv.innerHTML = "<h2>Error</h2><p>Something went wrong. Please try again.</p>";
    }
  });
</script>

</div>