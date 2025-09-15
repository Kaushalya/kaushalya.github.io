---
layout: default
title: Photo Tags
permalink: /photos/tags/
---

<h1>{{ page.title }}</h1>

<div id="tag-list">
  {% assign all_tags = "" | split: "" %}
  {% for photo in site.photos %}
    {% for tag in photo.tags %}
      {% assign all_tags = all_tags | push: tag %}
    {% endfor %}
  {% endfor %}
  {% assign unique_tags = all_tags | uniq | sort %}

  <button class="tag-button" data-tag="all">Show All</button>
  {% for tag in unique_tags %}
    <button class="tag-button" data-tag="{{ tag }}">#{{ tag }}</button>
  {% endfor %}
</div>

<div id="photo-grid" style="display: grid; grid-template-columns: repeat(auto-fill, minmax(250px, 1fr)); gap: 1rem; margin-top: 2rem;">
  {% for photo in site.photos reversed %}
    <a href="{{ photo.url | relative_url }}" class="photo-item" data-tags="{{ photo.tags | join: ' ' }}" style="text-decoration: none;">
      <div class="photo-thumbnail">
        <img src="{{ photo.images[0] | relative_url }}" alt="{{ photo.title }}" style="width: 100%; height: 200px; object-fit: cover;">
        <h3 style="margin-top: 0.5rem; font-size: 1rem;">{{ photo.title }}</h3>
      </div>
    </a>
  {% endfor %}
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const buttons = document.querySelectorAll('.tag-button');
  const photoItems = document.querySelectorAll('.photo-item');
  const grid = document.getElementById('photo-grid');

  function filterPhotos(tag) {
    let hasVisiblePhotos = false;
    photoItems.forEach(item => {
      const itemTags = item.dataset.tags.split(' ');
      if (tag === 'all' || itemTags.includes(tag)) {
        item.style.display = 'block';
        hasVisiblePhotos = true;
      } else {
        item.style.display = 'none';
      }
    });
    // You can add a "no results" message here if needed
  }

  buttons.forEach(button => {
    button.addEventListener('click', () => {
      const selectedTag = button.dataset.tag;
      filterPhotos(selectedTag);
      // Update URL hash
      window.location.hash = selectedTag;
    });
  });

  // Check for a hash on page load
  const currentHash = window.location.hash.substring(1);
  if (currentHash) {
    filterPhotos(currentHash);
  }
});
</script>

<style>
.tag-button { margin: 0.25rem; }
/* Add some active styling for the selected button if you like */
</style>