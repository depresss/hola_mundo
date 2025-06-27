<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Compra JDCoin</title>
  <script src="https://cdn.jsdelivr.net/npm/web3@latest/dist/web3.min.js"></script>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; background-color: #f2f2f2; }
    .card { background: white; padding: 20px; border-radius: 10px; max-width: 500px; margin: auto; box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
    .title { font-size: 1.5rem; margin-bottom: 10px; }
    .btn { padding: 10px 20px; margin: 5px; border: none; border-radius: 5px; cursor: pointer; }
    .eth { background-color: #4caf50; color: white; }
    .izipay { background-color: #1a73e8; color: white; }
    .yape { background-color: purple; color: white; }
    .input { width: 100%; padding: 10px; margin-top: 10px; margin-bottom: 10px; border-radius: 5px; border: 1px solid #ccc; }
  </style>
</head>
<body>
  <div class="card">
    <div class="title">Comprar JDCoin (JDC)</div>
    <label>Wallet del comprador:</label>
    <input id="wallet" type="text" class="input" placeholder="0x..." />

    <label>Cantidad de JDC a comprar:</label>
    <input id="cantidad" type="number" class="input" placeholder="Ej: 100" />

    <div>
      <button class="btn eth" onclick="comprarConCoinbase()">Pagar con Cripto (Coinbase)</button>
      <button class="btn izipay" onclick="pagarConIzipay()">Pagar con Tarjeta / Yape (Izipay)</button>
      <button class="btn yape" onclick="pagoManual()">Pago Manual (Yape / Plin)</button>
    </div>

    <p id="estado" style="margin-top: 20px; color: green;"></p>
  </div>

  <script>
    const tokenAddress = "0x1234567890abcdef..."; // Reemplazar por el real
    const tokenAbi = [ /* tu ABI aquí */ ];
    const precioPorToken = 0.1; // en USD por token

    async function comprarConCoinbase() {
      const wallet = document.getElementById("wallet").value;
      const cantidad = parseInt(document.getElementById("cantidad").value);
      if (!wallet || !cantidad) return alert("Completa todos los campos");

      window.open("https://commerce.coinbase.com/checkout/tu-checkout-id", "_blank");
      document.getElementById("estado").innerText = "Redirigido a Coinbase para completar el pago...";
    }

    function pagarConIzipay() {
      const wallet = document.getElementById("wallet").value;
      const cantidad = parseInt(document.getElementById("cantidad").value);
      if (!wallet || !cantidad) return alert("Completa todos los campos");

      const monto = cantidad * precioPorToken;
      window.open("https://tu-pasarela-izipay.com/pagar?monto=" + monto, "_blank");
      document.getElementById("estado").innerText = "Procesando pago con Izipay...";
    }

    function pagoManual() {
      const wallet = document.getElementById("wallet").value;
      const cantidad = parseInt(document.getElementById("cantidad").value);
      if (!wallet || !cantidad) return alert("Completa todos los campos");

      alert("Realiza tu pago por Yape o Plin al número XXXXXXXXX. Una vez confirmado, enviaremos los JDC a tu wallet: " + wallet);
      document.getElementById("estado").innerText = "Esperando confirmación manual del pago...";
    }
  </script>
</body>
</html>
