/* Halevi Enterprises — Main JS */

(function () {
  "use strict";

  /* ---- Theme Toggle ---- */
  var toggle = document.querySelector("[data-theme-toggle]");
  var root = document.documentElement;
  var theme = window.matchMedia("(prefers-color-scheme: dark)").matches
    ? "dark"
    : "light";

  root.setAttribute("data-theme", theme);
  updateToggleIcon();

  if (toggle) {
    toggle.addEventListener("click", function () {
      theme = theme === "dark" ? "light" : "dark";
      root.setAttribute("data-theme", theme);
      toggle.setAttribute(
        "aria-label",
        "Switch to " + (theme === "dark" ? "light" : "dark") + " mode"
      );
      updateToggleIcon();
    });
  }

  function updateToggleIcon() {
    if (!toggle) return;
    toggle.innerHTML =
      theme === "dark"
        ? '<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="5"/><path d="M12 1v2M12 21v2M4.22 4.22l1.42 1.42M18.36 18.36l1.42 1.42M1 12h2M21 12h2M4.22 19.78l1.42-1.42M18.36 5.64l1.42-1.42"/></svg>'
        : '<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>';
  }

  /* ---- Mobile Menu Toggle ---- */
  var mobileToggle = document.querySelector("[data-mobile-toggle]");
  var mobileNav = document.querySelector("[data-mobile-nav]");

  if (mobileToggle && mobileNav) {
    mobileToggle.addEventListener("click", function () {
      var isOpen = mobileNav.classList.contains("active");
      mobileNav.classList.toggle("active");
      mobileNav.setAttribute("aria-hidden", isOpen ? "true" : "false");
      mobileToggle.setAttribute("aria-expanded", isOpen ? "false" : "true");
      mobileToggle.innerHTML = isOpen
        ? '<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 12h18M3 6h18M3 18h18"/></svg>'
        : '<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 6L6 18M6 6l12 12"/></svg>';
    });
  }

  /* ---- Header Scroll Shadow ---- */
  var header = document.getElementById("header");
  var lastScroll = 0;

  function onScroll() {
    var scrollY = window.scrollY;
    if (header) {
      if (scrollY > 20) {
        header.classList.add("header--scrolled");
      } else {
        header.classList.remove("header--scrolled");
      }
    }
    lastScroll = scrollY;
  }

  window.addEventListener("scroll", onScroll, { passive: true });
  onScroll();

  /* ---- Smooth Scroll for Anchor Links ---- */
  document.querySelectorAll('a[href^="#"]').forEach(function (anchor) {
    anchor.addEventListener("click", function (e) {
      var targetId = this.getAttribute("href");
      if (targetId === "#") return;
      var target = document.querySelector(targetId);
      if (target) {
        e.preventDefault();
        /* Close mobile nav if open */
        if (mobileNav && mobileNav.classList.contains("active")) {
          mobileNav.classList.remove("active");
          mobileNav.setAttribute("aria-hidden", "true");
          if (mobileToggle) {
            mobileToggle.setAttribute("aria-expanded", "false");
            mobileToggle.innerHTML =
              '<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 12h18M3 6h18M3 18h18"/></svg>';
          }
        }
        target.scrollIntoView({ behavior: "smooth", block: "start" });
      }
    });
  });

  /* ---- Fade-in on scroll using IntersectionObserver ---- */
  var fadeEls = document.querySelectorAll(".fade-in");
  if (fadeEls.length > 0 && "IntersectionObserver" in window) {
    fadeEls.forEach(function (el) {
      el.classList.add("fade-in--pending");
    });

    var observer = new IntersectionObserver(
      function (entries) {
        entries.forEach(function (entry) {
          if (entry.isIntersecting) {
            entry.target.classList.remove("fade-in--pending");
            entry.target.classList.add("fade-in--visible");
            observer.unobserve(entry.target);
          }
        });
      },
      { threshold: 0.08, rootMargin: "0px 0px -40px 0px" }
    );

    fadeEls.forEach(function (el) {
      observer.observe(el);
    });
  }
})();
