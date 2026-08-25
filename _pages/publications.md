---
layout: page
permalink: /publications/
title: PUBLICATIONS
#description: Publications in reversed chronological order.
nav: true
nav_order: 2
---

<!-- _pages/publications.md -->

<!-- Bibsearch Feature -->

<!-- {% include bib_search.liquid %} -->

<style>
  .pub-filter-buttons .btn {
    transition: all 0.2s ease;
  }

  .pub-filter-buttons .btn.active {
    background-color: var(--global-theme-color);
    border-color: var(--global-theme-color);
    color: white;
  }

  .pub-filter-buttons .btn:not(.active) {
    background-color: transparent;
    border-color: var(--global-theme-color);
    color: var(--global-theme-color);
  }
</style>

<div class="pub-filter-buttons mb-4">
  <button class="btn btn-outline-primary active" onclick="showPublications('all', this)">
    All
  </button>

  <button class="btn btn-outline-primary" onclick="showPublications('first', this)">
    First author
  </button>

  <button class="btn btn-outline-primary" onclick="showPublications('corresponding', this)">
    Corresponding author
  </button>
</div>

<p class="text-muted small mb-4">
  * Equal contribution / co-first author &nbsp;&nbsp; ✉ Corresponding author
</p>

<div id="pub-all" class="publications pub-group">
  {% bibliography %}
</div>

<div id="pub-first" class="publications pub-group" style="display: none;">
  {% bibliography --query @*[keywords~=first-author] %}
</div>

<div id="pub-corresponding" class="publications pub-group" style="display: none;">
  {% bibliography --query @*[keywords~=corresponding-author] %}
</div>

<script>
  function showPublications(group, button) {
    document.querySelectorAll(".pub-group").forEach(function (element) {
      element.style.display = "none";
    });

    document.getElementById("pub-" + group).style.display = "block";

    document.querySelectorAll(".pub-filter-buttons button").forEach(function (element) {
      element.classList.remove("active");
    });

    button.classList.add("active");
  }
</script>
