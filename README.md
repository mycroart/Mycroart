<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Mycro Arts | Micro Art</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(120deg, #ffecd2, #fcb69f);
      color: #333;
    }

    header {
      background: #ff5e57;
      color: white;
      text-align: center;
      padding: 1.5rem 1rem;
      font-size: 2rem;
      font-weight: bold;
      box-shadow: 0 2px 5px rgba(0,0,0,0.2);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 1rem;
    }

    header img {
      height: 50px;
      width: 50px;
      border-radius: 50%;
    }

    .container {
      padding: 2rem;
      max-width: 800px;
      margin: auto;
      background: white;
      border-radius: 12px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    }

    h2 {
      color: #ff5e57;
    }

    .scroll-gallery-wrapper {
      overflow: hidden;
      height: 220px;
      position: relative;
      margin-bottom: 2rem;
    }

    .scroll-row {
      display: flex;
      width: max-content;
      gap: 1rem;
      animation: scroll-left 20s linear infinite;
    }

    .scroll-row.reverse {
      animation: scroll-right 25s linear infinite;
      margin-top: 1rem;
    }

    .scroll-row img {
      width: 200px;
      height: 200px;
      object-fit: cover;
      border-radius: 12px;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.2);
    }

    @keyframes scroll-left {
      0% { transform: translateX(0); }
      100% { transform: translateX(-50%); }
    }

    @keyframes scroll-right {
      0% { transform: translateX(0); }
      100% { transform: translateX(50%); }
    }

    form {
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }

    input, select, textarea {
      padding: 0.7rem;
      border-radius: 8px;
      border: 1px solid #ccc;
      font-size: 1rem;
    }

    button {
      background: #ff5e57;
      color: white;
      padding: 0.9rem;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-size: 1rem;
    }

    .note {
      background: #ffe0dc;
      padding: 1rem;
      border-radius: 8px;
      margin-top: 1rem;
      font-size: 0.95rem;
    }

    footer {
      text-align: center;
      margin-top: 3rem;
      padding: 1rem;
      font-size: 0.9rem;
      color: #555;
    }

    footer a {
      color: #ff5e57;
      text-decoration: none;
    }

    .success-message {
      color: green;
      margin-top: 1rem;
      font-weight: bold;
    }

    .error-message {
      color: red;
      margin-top: 1rem;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <header>
    <img src="mycrologo.png" alt="Mycro Arts Logo">
    Mycro Arts – Tiny Masterpieces
  </header>

  <div class="container">
    <h2>🎨 Our Work</h2>
    <div class="scroll-gallery-wrapper">
      <div class="scroll-row">
        <img src="sample1.jpg" alt="Micro Art 1">
        <img src="sample2.jpg" alt="Micro Art 2">
        <img src="sample3.jpg" alt="Micro Art 3">
        <img src="sample4.jpg" alt="Micro Art 4">
        <img src="sample1.jpg" alt="Micro Art 1">
        <img src="sample2.jpg" alt="Micro Art 2">
      </div>
      <div class="scroll-row reverse">
        <img src="sample3.jpg" alt="Micro Art 3">
        <img src="sample4.jpg" alt="Micro Art 4">
        <img src="sample2.jpg" alt="Micro Art 2">
        <img src="sample1.jpg" alt="Micro Art 1">
        <img src="sample4.jpg" alt="Micro Art 4">
        <img src="sample3.jpg" alt="Micro Art 3">
      </div>
    </div>

    <h2>🛒 Place Your Order</h2>
    <form id="orderForm" onsubmit="sendMail(); return false;">
      <input type="text" id="name" name="name" placeholder="Your Name" required />
      <input type="tel" id="phone" name="phone" placeholder="Phone Number" required />
      <input type="text" id="location" name="location" placeholder="Location" required />
      <input type="text" id="pincode" name="pincode" placeholder="Pincode" required />

      <label for="product">Type of Product:</label>
      <select id="product" name="product" required>
        <option value="">-- Select --</option>
        <option value="chalk">Chalk Art (Custom Name)</option>
        <option value="pencil">Pencil Lid Art (Custom Name)</option>
      </select>

      <textarea id="request" name="request" placeholder="Any special request?" rows="3"></textarea>

      <button type="submit">Submit Request</button>
      <p id="responseMessage"></p>
    </form>

    <div class="note">
      📍 <strong>Order Method:</strong><br>
      1. Direct message us on Instagram: <a href="https://instagram.com/mycro_arts" target="_blank">@mycro_arts</a><br>
      2. Web page order available only for <strong>Nagapattinam-611 101</strong> surroundings (District of Tamil Nadu)<br><br>
      📧 Email: <a href="mailto:miiicroartz@gmail.com">miiicroartz@gmail.com</a>
    </div>
  </div>

  <footer>
    © 2025 Mycro Arts | Designed with ❤️ by 
    <a href="https://instagram.com/perf.cut" target="_blank">Perfcut</a>
  </footer>

  <!-- EmailJS Script -->
  <script src="https://cdn.emailjs.com/dist/email.min.js"></script>
  <script>
    (function() {
      emailjs.init("xQ7QIVsWyjaThv_u9");
    })();

    function sendMail() {
      var params = {
        name: document.getElementById("name").value,
        phone: document.getElementById("phone").value,
        location: document.getElementById("location").value,
        pincode: document.getElementById("pincode").value,
        product: document.getElementById("product").value,
        request: document.getElementById("request").value,
      };

      emailjs.send("service_formycro", "template_yrp8xsf", params)
        .then(function(response) {
          document.getElementById("responseMessage").textContent = "✅ Your order has been placed successfully!";
          document.getElementById("responseMessage").className = "success-message";
          document.getElementById("orderForm").reset();
        }, function(error) {
          document.getElementById("responseMessage").textContent = "❌ Order failed. Please try again.";
          document.getElementById("responseMessage").className = "error-message";
          console.error("EmailJS Error:", error);
        });
    }
  </script>

</body>
</html>
