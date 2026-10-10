// Ganti alamat di bawah dengan email aktif kamu sebelum website dipublikasikan.
const CONTACT_EMAIL = "ganti-email-kamu@example.com";

document.getElementById("year").textContent = new Date().getFullYear();

const menuToggle = document.getElementById("menuToggle");
const navMenu = document.getElementById("navMenu");
menuToggle.addEventListener("click", () => {
  const isOpen = navMenu.classList.toggle("open");
  menuToggle.setAttribute("aria-expanded", String(isOpen));
  menuToggle.textContent = isOpen ? "✕" : "☰";
});

document.querySelectorAll("#navMenu a").forEach(link => {
  link.addEventListener("click", () => {
    navMenu.classList.remove("open");
    menuToggle.setAttribute("aria-expanded", "false");
    menuToggle.textContent = "☰";
  });
});

const revealObserver = new IntersectionObserver(entries => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add("visible");
      revealObserver.unobserve(entry.target);
    }
  });
}, { threshold: 0.12 });
document.querySelectorAll(".reveal").forEach(el => revealObserver.observe(el));

const sections = document.querySelectorAll("main section[id]");
const navLinks = document.querySelectorAll(".nav-link");
const activeObserver = new IntersectionObserver(entries => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      navLinks.forEach(link => {
        link.classList.toggle("active", link.getAttribute("href") === `#${entry.target.id}`);
      });
    }
  });
}, { rootMargin: "-35% 0px -55% 0px" });
sections.forEach(section => activeObserver.observe(section));

document.getElementById("contactForm").addEventListener("submit", event => {
  event.preventDefault();
  if (!CONTACT_EMAIL || CONTACT_EMAIL === "ganti-email-kamu@example.com") {
    alert("Min, edit dulu CONTACT_EMAIL di file script.js dengan email tujuan kamu ya.");
    return;
  }
  const form = new FormData(event.currentTarget);
  const name = form.get("name");
  const email = form.get("email");
  const message = form.get("message");
  const subject = encodeURIComponent(`Pesan portofolio dari ${name}`);
  const body = encodeURIComponent(`Nama: ${name}\nEmail: ${email}\n\n${message}`);
  window.location.href = `mailto:${CONTACT_EMAIL}?subject=${subject}&body=${body}`;
});
