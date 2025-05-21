# covid_globaltracker
// Button click
document.getElementById('magicBtn').addEventListener('click', function() {
  this.textContent = 'Clicked!';
  this.style.background = '#8bc34a';
});

// Hover effect
document.getElementById('galleryImg').addEventListener('mouseenter', function() {
  this.classList.add('animated');
});
document.getElementById('galleryImg').addEventListener('mouseleave', function() {
  this.classList.remove('animated');
});

// Keypress detection
document.addEventListener('keydown', function(e) {
  if (e.key === 'a') alert('You pressed "a"!');
});

// Double-click secret action
document.getElementById('magicBtn').addEventListener('dblclick', function() {
  alert('Secret double-click!');
});

// Image gallery
const images = [
  'https://placekitten.com/200/200',
  'https://placekitten.com/201/200',
  'https://placekitten.com/202/200'
];
let imgIndex = 0;
document.getElementById('prevImg').onclick = function() {
  imgIndex = (imgIndex - 1 + images.length) % images.length;
  document.getElementById('galleryImg').src = images[imgIndex];
};
document.getElementById('nextImg').onclick = function() {
  imgIndex = (imgIndex + 1) % images.length;
  document.getElementById('galleryImg').src = images[imgIndex];
};

// Tabs
document.querySelectorAll('.tab').forEach(tab => {
  tab.onclick = function() {
    document.querySelectorAll('.tab-content').forEach(tc => tc.style.display = 'none');
    document.getElementById('tab' + this.dataset.tab).style.display = 'block';
  };
});

// Form validation
const emailInput = document.getElementById('email');
const passwordInput = document.getElementById('password');
const feedback = document.getElementById('formFeedback');

function validateEmail(email) {
  return /\S+@\S+\.\S+/.test(email);
}

function validatePassword(pw) {
  return pw.length >= 8;
}

emailInput.addEventListener('input', function() {
  feedback.textContent = validateEmail(this.value) ? '' : 'Invalid email format';
});
passwordInput.addEventListener('input', function() {
  feedback.textContent = validatePassword(this.value) ? '' : 'Password must be at least 8 characters';
});

document.getElementById('signupForm').addEventListener('submit', function(e) {
  e.preventDefault();
  if (!validateEmail(emailInput.value)) {
    feedback.textContent = 'Please enter a valid email.';
    return;
  }
  if (!validatePassword(passwordInput.value)) {
    feedback.textContent = 'Password must be at least 8 characters.';
    return;
  }
  feedback.textContent = 'Success!';
});
