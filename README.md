# Quick-repayment
-- FILE: README.md --

Quick Repay (Two-page static website)

Simple, fast, mobile-first two-page website to list loan products and let users copy UPI IDs to pay.

Included files:

index.html  — Loan products list with "Repay" buttons

repay.html  — Copy-UPI page (shows provided UPI IDs with Copy buttons)

styles.css  — Small extra CSS (Tailwind CDN is used)

script.js   — Clipboard + small UI scripts

assets/     — Put your logo images here: paytm.png, phonepe.png, gpay.png, logo.png


How to deploy on GitHub Pages:

1. Create a new GitHub repository (public).


2. Copy these files into the repo root (keep the assets/ folder).


3. Commit & push.


4. In repo settings -> Pages -> choose main branch and / (root) folder -> Save. The site will be available at https://<username>.github.io/<repo>/ (or your custom redirect service).



Fast test locally: open index.html in a browser. No build step required.

-- FILE: index.html -- <!doctype html>

<html lang="bn">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Quick Repay — Loan Products</title>
  <meta name="description" content="Quick Repay — fast UPI copy page for loan repayments">
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
  <link rel="stylesheet" href="styles.css">
</head>
<body class="bg-gray-50 text-gray-900">
  <header class="bg-white shadow-sm">
    <div class="max-w-3xl mx-auto px-4 py-5 flex items-center gap-4">
      <img src="assets/logo.png" alt="logo" class="w-12 h-12 rounded-md object-cover">
      <div>
        <h1 class="text-2xl font-extrabold">Quick Repay</h1>
        <p class="text-sm text-gray-500">Fast loan repayment — copy UPI and pay</p>
      </div>
      <a href="https://whapka.shorts.gy/Rhdhsh" class="ml-auto text-xs px-3 py-1 border rounded-full text-blue-600 border-blue-200">Domain</a>
    </div>
  </header>  <main class="max-w-3xl mx-auto px-4 py-6">
    <section class="mb-6">
      <h2 class="text-lg font-semibold mb-2">Loans product here</h2>
      <p class="text-sm text-gray-500 mb-4">Tap "Repay" for the product you want to pay for — then copy the UPI ID on the next page.</p><ul class="grid gap-3">
    <!-- Example loan list: you can edit these names in the HTML directly -->
    <li class="card flex items-center justify-between px-4 py-3 bg-white rounded-lg shadow-sm">
      <div class="flex items-center gap-3">
        <div class="w-10 h-10 bg-yellow-100 rounded-full flex items-center justify-center text-yellow-700 font-bold">₹</div>
        <div>
          <div class="font-medium">Karta Loan</div>
          <div class="text-xs text-gray-500">₹5,000 - ₹50,000</div>
        </div>
      </div>
      <a class="repay-btn inline-block px-4 py-2 bg-blue-600 text-white rounded-lg font-medium" href="repay.html?product=Karta%20Loan">Repay</a>
    </li>

    <li class="card flex items-center justify-between px-4 py-3 bg-white rounded-lg shadow-sm">
      <div class="flex items-center gap-3">
        <div class="w-10 h-10 bg-yellow-100 rounded-full flex items-center justify-center text-yellow-700 font-bold">₹</div>
        <div>
          <div class="font-medium">Speed Loan</div>
          <div class="text-xs text-gray-500">Instant small loans</div>
        </div>
      </div>
      <a class="repay-btn inline-block px-4 py-2 bg-blue-600 text-white rounded-lg font-medium" href="repay.html?product=Speed%20Loan">Repay</a>
    </li>

    <li class="card flex items-center justify-between px-4 py-3 bg-white rounded-lg shadow-sm">
      <div class="flex items-center gap-3">
        <div class="w-10 h-10 bg-yellow-100 rounded-full flex items-center justify-center text-yellow-700 font-bold">₹</div>
        <div>
          <div class="font-medium">Credit Guru</div>
          <div class="text-xs text-gray-500">Revolving credit</div>
        </div>
      </div>
      <a class="repay-btn inline-block px-4 py-2 bg-blue-600 text-white rounded-lg font-medium" href="repay.html?product=Credit%20Guru">Repay</a>
    </li>

    <!-- ADD more items as needed -->

  </ul>

</section>

<section class="mt-6 text-center bg-lime-200 rounded-lg p-4">
  <h3 class="font-semibold mb-2">Tips:</h3>
  <ol class="list-decimal list-inside text-left max-w-md mx-auto">
    <li>Click Repay</li>
    <li>Copy any UPI</li>
    <li>Pay with any payment app</li>
  </ol>
</section>

  </main>  <script src="script.js"></script></body>
</html>-- FILE: repay.html -- <!doctype html>

<html lang="bn">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Quick Repay — Copy UPI</title>
  <meta name="description" content="Copy UPI ID to clipboard for quick repayment">
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
  <link rel="stylesheet" href="styles.css">
</head>
<body class="bg-gray-50 text-gray-900">
  <header class="bg-white shadow-sm">
    <div class="max-w-3xl mx-auto px-4 py-5 flex items-center gap-4">
      <img src="assets/logo.png" alt="logo" class="w-10 h-10 rounded-md object-cover">
      <div>
        <h1 class="text-2xl font-extrabold">Quick Repay</h1>
        <p class="text-sm text-gray-500">Copy this UPI</p>
      </div>
      <a href="index.html" class="ml-auto text-sm px-3 py-1 border rounded-full text-gray-700 border-gray-200">Back</a>
    </div>
  </header>  <main class="max-w-3xl mx-auto px-4 py-6">
    <section class="text-center mb-6">
      <h2 class="text-xl font-bold">Copy this UPI</h2>
      <p id="product-name" class="text-sm text-gray-500 mt-1"></p>
    </section><section class="space-y-3">
  <!-- UPI cards -->
  <div class="upi-card flex items-center justify-between p-4 bg-white rounded-lg shadow-sm">
    <div class="text-lg font-medium" id="upi-1">archerykashihills-7@okaxis</div>
    <button class="copy-btn px-4 py-2 rounded-lg bg-blue-600 text-white" data-upi="archerykashihills-7@okaxis">Copy</button>
  </div>

  <div class="upi-card flex items-center justify-between p-4 bg-white rounded-lg shadow-sm">
    <div class="text-lg font-medium" id="upi-2">r.biswas.11@superyes</div>
    <button class="copy-btn px-4 py-2 rounded-lg bg-blue-600 text-white" data-upi="r.biswas.11@superyes">Copy</button>
  </div>

  <div class="upi-card flex items-center justify-between p-4 bg-white rounded-lg shadow-sm">
    <div class="text-lg font-medium" id="upi-3">9678209465@upi</div>
    <button class="copy-btn px-4 py-2 rounded-lg bg-blue-600 text-white" data-upi="9678209465@upi">Copy</button>
  </div>
</section>

<section class="mt-8">
  <h3 class="font-bold mb-3">Pay with :</h3>
  <div class="flex items-center gap-6">
    <img src="assets/paytm.png" alt="Paytm" class="h-10">
    <img src="assets/phonepe.png" alt="PhonePe" class="h-10">
    <img src="assets/gpay.png" alt="GPay" class="h-10">
  </div>
</section>

<div id="toast" class="fixed left-1/2 transform -translate-x-1/2 bottom-8 bg-gray-900 text-white px-4 py-2 rounded-lg opacity-0 pointer-events-none transition-opacity"></div>

  </main>  <script src="script.js"></script></body>
</html>-- FILE: styles.css -- /* small extra styles to enhance look */ body { -webkit-font-smoothing:antialiased; } .card { border: 1px solid rgba(0,0,0,0.03); } .upi-card { transition: transform .08s ease, box-shadow .08s ease; } .upi-card:hover { transform: translateY(-2px); box-shadow: 0 6px 18px rgba(16,24,40,0.06); } .copy-btn:active { transform: scale(.98); } #toast.show { opacity: 1; pointer-events: auto; }

-- FILE: script.js -- // Small JS: get product from query param, copy to clipboard with feedback (function(){ function qs(name){ return new URLSearchParams(location.search).get(name); } var product = qs('product'); if(product){ var el = document.getElementById('product-name'); if(el) el.textContent = 'Product: ' + decodeURIComponent(product); }

function showToast(msg){ var t = document.getElementById('toast'); if(!t) return; t.textContent = msg; t.classList.add('show'); setTimeout(function(){ t.classList.remove('show'); }, 2000); }

// attach copy handlers document.addEventListener('click', function(e){ var btn = e.target.closest && e.target.closest('.copy-btn'); if(!btn) return; var upi = btn.getAttribute('data-upi') || btn.dataset.upi; if(!upi) return; // use clipboard API if(navigator.clipboard && navigator.clipboard.writeText){ navigator.clipboard.writeText(upi).then(function(){ showToast('UPI copied: ' + upi); }).catch(function(){ fallbackCopy(upi); }); } else { fallbackCopy(upi); } });

function fallbackCopy(text){ var ta = document.createElement('textarea'); ta.value = text; ta.setAttribute('readonly',''); ta.style.position = 'absolute'; ta.style.left = '-9999px'; document.body.appendChild(ta); ta.select(); try{ document.execCommand('copy'); showToast('UPI copied: ' + text); }catch(e){ alert('Copy failed. UPI: ' + text); } document.body.removeChild(ta); } })();

-- FILE: assets/README.txt -- Put these images into the assets folder (recommended sizes around 200x200 or 300x100):

logo.png        (your site logo)

paytm.png       (Paytm logo)

phonepe.png     (PhonePe logo)

gpay.png        (GPay / Google Pay logo)


You can replace the images with transparent PNGs for the best look.

-- EOF --
