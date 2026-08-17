---
layout: about
title: about
permalink: /
# subtitle: Researcher at <a href='https://www.supcon.com/'>Supcon</a>

profile:
  align: right
  image: photo.jpg
  image_circular: false # crops the image to make it circular
  # more_info: FIT Building, THU

selected_papers: true # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: false # includes a list of news items
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

latest_posts:
  enabled: false
  scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts
---

HI! I am a researcher at <a href="https://www.supcon.com/" target="_blank">Supcon</a> working on Industrial AI. Our team is building a suite of industrial intelligent agents fostering innovation in industrial intelligence.

My current work mainly focuses on constructing ontology-based agents using hyper-graphs and harness engineering to encapsulate enterprise knowledge, business entities, and operational logic. This enables structured reasoning and task planning while preserving explainability and execution determinism. I am also interested in graph foundation models (GFMs), bridging the gap between cutting-edge AI research and real-world industrial applications.

Before joining Supcon, I received my Ph.D. from <a href="https://www.tsinghua.edu.cn/" target="_blank">Tsinghua University</a> in 2025, advised by <a href="https://iiis.tsinghua.edu.cn/rydw/qzjs/xmc/index.htm" target="_blank">Professor M. Chen</a>.

<!-- Please feel free to contact me — <a href="mailto:liuxin4@supcon.com">liuxin4@supcon.com</a> &middot; <a href="mailto:greenliuxin@163.com">greenliuxin@163.com</a> -->

{% comment %}
<!-- Small visitor map (client-side GeoIP, opt-out) -->
<hr style="margin-top:1.25rem; margin-bottom:0.75rem;">
<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
<div id="about-visitor-map" style="height:220px; max-width:640px; border:1px solid #ddd; border-radius:6px; margin-top:0.5rem;"></div>
<p id="about-visitor-status" style="margin-top:0.4rem; font-size:0.95rem;">
  This small map shows an approximate location based on your IP address. No IPs are stored.
  <label style="margin-left:0.8rem"><input type="checkbox" id="about-optout"> Opt out</label>
</p>

<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
<script>
(function () {
  const OPT_KEY = 'visitor_map_optout';
  const optoutCheckbox = document.getElementById('about-optout');
  try { optoutCheckbox.checked = localStorage.getItem(OPT_KEY) === '1'; } catch (e) {}
  optoutCheckbox.addEventListener('change', () => {
    try { localStorage.setItem(OPT_KEY, optoutCheckbox.checked ? '1' : '0'); } catch (e) {}
  });

  if (optoutCheckbox.checked) {
    document.getElementById('about-visitor-status').textContent = 'You have opted out of location lookup.';
    return;
  }

  const map = L.map('about-visitor-map', { zoomControl: false }).setView([20, 0], 2);
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors',
    maxZoom: 18
  }).addTo(map);

  const statusEl = document.getElementById('about-visitor-status');
  statusEl.textContent = 'Determining approximate location…';

  fetch('https://ipapi.co/json/')
    .then(r => r.ok ? r.json() : Promise.reject('geoip failed'))
    .then(data => {
      const lat = data.latitude || data.lat;
      const lon = data.longitude || data.lon;
      const city = data.city || '';
      const region = data.region || '';
      const country = data.country_name || data.country || '';
      if (lat && lon) {
        const marker = L.circleMarker([lat, lon], { radius: 6 }).addTo(map);
        marker.bindPopup([city, region, country].filter(Boolean).join(', ') || 'Unknown location');
        map.setView([lat, lon], 6);
        statusEl.textContent = 'Approximate location shown (based on IP).';
      } else {
        statusEl.textContent = 'Location data unavailable.';
      }
    })
    .catch(() => {
      statusEl.textContent = 'Unable to determine location.';
    });
})();
</script>
{% endcomment %}
