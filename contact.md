---
layout: page
title: Contact &amp; Booking
permalink: /contact/
---

<div class="contact-grid">
  <div class="contact-info">
    <h2>Get in Touch</h2>
    <p>Ready to book a tour or have a question? We typically respond within a few hours during business hours (Mon–Sun, 08:00–20:00 CET).</p>

    <ul class="contact-details">
      <li>
        <i class="fas fa-map-marker-alt"></i>
        <div>
          <strong>Meeting point</strong><br>
          Plaza de Cibeles, Madrid, Spain<br>
          <em>(exact location sent after booking)</em>
        </div>
      </li>
      <li>
        <i class="fas fa-envelope"></i>
        <div>
          <strong>Email</strong><br>
          <a href="mailto:info@madridbketours.com">info@madridbketours.com</a>
        </div>
      </li>
      <li>
        <i class="fas fa-phone"></i>
        <div>
          <strong>Phone / WhatsApp</strong><br>
          +34 600 000 000
        </div>
      </li>
    </ul>

    <div class="contact-social">
      <a href="https://instagram.com/madridbketours" target="_blank" rel="noopener">
        <i class="fab fa-instagram"></i> @madridbketours
      </a>
    </div>
  </div>

  <div class="contact-form-wrapper">
    <h2>Book a Tour</h2>
    <form class="contact-form" action="https://formspree.io/f/maqraanv" method="POST">
      <div class="form-group">
        <label for="name">Full Name *</label>
        <input type="text" id="name" name="name" required placeholder="Your name">
      </div>
      <div class="form-group">
        <label for="email">Email *</label>
        <input type="email" id="email" name="email" required placeholder="your@email.com">
      </div>
      <div class="form-group">
        <label for="tour">Tour</label>
        <select id="tour" name="tour">
          <option value="">Select a tour…</option>
          {% for tour in site.tours %}
          <option value="{{ tour.title }}">{{ tour.title }}</option>
          {% endfor %}
          <option value="custom">Custom / Private Tour</option>
        </select>
      </div>
      <div class="form-row">
        <div class="form-group">
          <label for="date">Preferred Date *</label>
          <input type="date" id="date" name="date" required>
        </div>
        <div class="form-group">
          <label for="people">Number of People *</label>
          <input type="number" id="people" name="people" min="1" max="12" value="2" required>
        </div>
      </div>
      <div class="form-group">
        <label for="message">Message / Questions</label>
        <textarea id="message" name="message" rows="4" placeholder="Any special requirements, questions…"></textarea>
      </div>
      <button type="submit" class="btn btn-primary btn-block">Send Booking Request</button>
      <p class="form-note">* Required fields. We'll confirm your booking by email within 24 hours.</p>
    </form>
  </div>
</div>
