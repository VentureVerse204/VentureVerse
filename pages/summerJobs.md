# Summer 2025 Internships - Powered by VentureVerse 🚀  
Welcome to **VentureVerse's** curated list of **Summer 2025 tech internships**! 🌟 Whether you're searching for software engineering, product management, data science, or any tech-focused role, this list has you covered.

The internships in this repository are mainly located in **the United States, Canada, and Remote** positions. 🌍

💡 Be sure to visit our [Internship Success Guide](#) for tips on preparing your applications! 💡

---  
<div align="center">
    <h3>⚡ Stay in the loop! ⚡</h3>
    <p>Get updates on new internships straight to your inbox:</p>
    <a href="https://ventureverse-updates.com">
        <img src="https://via.placeholder.com/400x150?text=Sign+Up+for+Internship+Updates" alt="Sign Up for Updates" width="400">
    </a>
    <p>We'd love to see your internship success stories, so tag us on social media!</p>
</div>

---

<div align="center">
    <p><strong>Apply with ease!</strong></p>
    <p>Make your application process smoother by checking out our <a href="https://ventureverse.com/internships">Internship Helper Tool</a>.</p>
    <a href="https://ventureverse.com/internships">
        <img src="https://via.placeholder.com/450x150?text=One+Click+Internship+Applications" alt="One-Click Apply" width="450">
    </a>
</div>

---

## Internship List 🔍

<div id="internship-list">
  <!-- Internship table will be dynamically loaded here -->
</div>

<div align="center">
  <button id="loadMore" onclick="loadMore()">Show More Internships</button>
</div>

---

## How to Navigate 📜
- **Internship Listings**: Find a comprehensive list of Summer 2025 internships [here](./internships.json).
- **New Grad Positions**: View roles for recent graduates [here](./newgrad.json).
- **Case Competitions**: Discover active case competitions [here](./competitions.json).

---

<script>
// Fetch data from summerJobs.json and display top 30 internships
let internships = [];
let currentIndex = 0;
const ITEMS_PER_PAGE = 30;
const internshipListDiv = document.getElementById('internship-list');

function fetchInternships() {
  fetch('./scripts/summerListings.json')
    .then(response => response.json())
    .then(data => {
      internships = data; // Store the internships data
      displayInternships(); // Display the first set of internships
    })
    .catch(error => console.error('Error loading internships:', error));
}

function displayInternships() {
  let html = `
    <table>
      <tr>
        <th>Company</th>
        <th>Role</th>
        <th>Location</th>
        <th>Application Link</th>
        <th>Date Posted</th>
      </tr>
  `;

  const endIndex = Math.min(currentIndex + ITEMS_PER_PAGE, internships.length);
  for (let i = currentIndex; i < endIndex; i++) {
    const job = internships[i];
    html += `
      <tr>
        <td><a href="${job.company_url}">${job.company}</a></td>
        <td>${job.role}</td>
        <td>${job.location}</td>
        <td><a href="${job.apply_link}">Apply</a></td>
        <td>${job.date_posted}</td>
      </tr>
    `;
  }
  
  html += '</table>';
  internshipListDiv.innerHTML = html;
  currentIndex = endIndex; // Update the current index

  if (currentIndex >= internships.length) {
    document.getElementById('loadMore').style.display = 'none'; // Hide 'Show More' button if all items are displayed
  }
}

function loadMore() {
  displayInternships(); // Load next set of internships
}

// Initial load
fetchInternships();
</script>
