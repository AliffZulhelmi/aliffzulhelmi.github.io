---
layout: default
title: About Me
permalink: /about/
---

<div class="vcard">
  <div class="vcard-front">
    <h1>Muhammad Aliff Zulhelmi</h1>
    <p class="aka">Also Known As: MrChyper</p>
    <p class="occupation">Student at German-Malaysian Institute</p>
    <p class="course">Semester 1 Diploma In Cyber Security Technology</p>
    <div class="flip-instruction">Click to see interests</div>
  </div>
  <div class="vcard-back">
    <h2>Interests</h2>
    <ul>
      <li>Red-Team</li>
      <li>Malware Development/Analysis</li>
      <li>Web Penetration Testing</li>
      <li>Network Penetration Testing</li>
      <li>Web Development</li>
    </ul>
    <div class="flip-instruction">Click to flip back</div>
  </div>
</div>

<script>
document.querySelector('.vcard').addEventListener('click', function() {
  this.classList.toggle('flipped');
});
</script>