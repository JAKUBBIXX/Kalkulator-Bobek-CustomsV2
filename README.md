<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <title>Bar Sajgon - Kalkulator zestawów</title>

  <style>
    :root {
      --background-1: #07111f;
      --background-2: #111c30;
      --card: rgba(17, 27, 46, 0.88);
      --card-border: rgba(255, 255, 255, 0.09);
      --text: #f8fafc;
      --muted: #94a3b8;
      --accent: #22d3ee;
      --accent-2: #14b8a6;
      --danger: #fb7185;
      --shadow: rgba(0, 0, 0, 0.45);
    }

    * {
      box-sizing: border-box;
    }

    body {
      min-height: 100vh;
      margin: 0;
      padding: 24px;
      display: grid;
      place-items: center;
      overflow-x: hidden;
      font-family: Inter, Arial, sans-serif;
      color: var(--text);
      background:
        radial-gradient(circle at 10% 10%, rgba(34, 211, 238, 0.2), transparent 32%),
        radial-gradient(circle at 90% 90%, rgba(20, 184, 166, 0.17), transparent 30%),
        linear-gradient(135deg, var(--background-1), var(--background-2));
      transition: background 0.4s ease;
    }

    body::before {
      content: "";
      position: fixed;
      width: 300px;
      height: 300px;
      top: -130px;
      right: -100px;
      border-radius: 50%;
      background: rgba(34, 211, 238, 0.13);
      filter: blur(10px);
      pointer-events: none;
    }

    button,
    input {
      font: inherit;
    }

    button {
      border: 0;
      cursor: pointer;
      color: inherit;
    }

    .calculator {
      width: min(100%, 440px);
      padding: 32px;
      position: relative;
      overflow: hidden;
      text-align: center;
      border: 1px solid var(--card-border);
      border-radius: 28px;
      background: var(--card);
      box-shadow: 0 30px 70px var(--shadow);
      backdrop-filter: blur(18px);
    }

    .calculator::before {
      content: "";
      position: absolute;
      top: 0;
      left: 12%;
      width: 76%;
      height: 1px;
      background: linear-gradient(
        90deg,
        transparent,
        rgba(255, 255, 255, 0.7),
        transparent
      );
    }

    .logo {
      width: 72px;
      height: 72px;
      margin: 0 auto 14px;
      display: grid;
      place-items: center;
      border-radius: 22px;
      font-size: 38px;
      background: linear-gradient(135deg, #164e63, #0f766e);
      box-shadow: 0 12px 30px rgba(20, 184, 166, 0.25);
    }

    h1 {
      margin: 0;
      font-size: clamp(28px, 8vw, 38px);
      letter-spacing: -1px;
    }

    .subtitle {
      margin: 8px 0 26px;
      color: var(--muted);
    }

    .price-card {
      margin-bottom: 22px;
      padding: 14px 18px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      border: 1px solid rgba(255, 255, 255, 0.07);
      border-radius: 16px;
      background: rgba(255, 255, 255, 0.04);
    }

    .price-card span {
      color: var(--muted);
    }

    .price-card strong {
      font-size: 19px;
      color: var(--accent);
    }

    .counter {
      margin-bottom: 24px;
      display: grid;
      grid-template-columns: 62px 1fr 62px;
      align-items: center;
      gap: 15px;
    }

    .counter-button {
      width: 62px;
      height: 62px;
      border: 1px solid rgba(255, 255, 255, 0.1);
      border-radius: 18px;
      font-size: 31px;
      background: rgba(255, 255, 255, 0.07);
      transition: transform 0.15s ease, background 0.15s ease;
    }

    .counter-button:hover {
      background: rgba(34, 211, 238, 0.16);
    }

    .counter-button:active {
      transform: scale(0.92);
    }

    .count {
      font-size: 48px;
      font-weight: 800;
      line-height: 1;
      font-variant-numeric: tabular-nums;
    }

    .input-label {
      display: block;
      margin-bottom: 9px;
      text-align: left;
      color: var(--muted);
      font-size: 14px;
    }

    .number-input {
      width: 100%;
      padding: 14px 16px;
      border: 1px solid rgba(255, 255, 255, 0.1);
      border-radius: 14px;
      outline: none;
      text-align: center;
      font-size: 20px;
      color: var(--text);
      background: rgba(4, 10, 20, 0.45);
      transition: border-color 0.2s ease, box-shadow 0.2s ease;
    }

    .number-input:focus {
      border-color: var(--accent);
      box-shadow: 0 0 0 4px rgba(34, 211, 238, 0.12);
    }

    .summary {
      margin: 24px 0;
      padding: 21px;
      border: 1px solid rgba(34, 211, 238, 0.14);
      border-radius: 20px;
      background: linear-gradient(
        135deg,
        rgba(34, 211, 238, 0.09),
        rgba(20, 184, 166, 0.04)
      );
    }

    .summary-label {
      margin-bottom: 6px;
      color: var(--muted);
      font-size: 14px;
      text-transform: uppercase;
      letter-spacing: 1.5px;
    }

    .total {
      color: var(--accent);
      font-size: clamp(34px, 10vw, 45px);
      font-weight: 900;
      line-height: 1.15;
      font-variant-numeric: tabular-nums;
    }

    .selection {
      margin-top: 8px;
      color: var(--muted);
      font-size: 14px;
    }

    .discount-info {
      display: none;
      margin-top: 8px;
      color: #5eead4;
      font-size: 13px;
      font-weight: 700;
    }

    .discount-info.visible {
      display: block;
    }

    .actions {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
    }

    .action-button {
      min-height: 49px;
      padding: 11px 14px;
      border: 1px solid rgba(255, 255, 255, 0.09);
      border-radius: 14px;
      font-size: 14px;
      font-weight: 700;
      background: rgba(255, 255, 255, 0.07);
      transition: transform 0.15s ease, background 0.15s ease;
    }

    .action-button:hover {
      background: rgba(255, 255, 255, 0.12);
      transform: translateY(-2px);
    }

    .action-button.primary {
      color: #042f2e;
      background: linear-gradient(135deg, var(--accent), var(--accent-2));
    }

    .action-button.discount-active {
      color: #042f2e;
      border-color: transparent;
      background: #5eead4;
      box-shadow: 0 0 24px rgba(94, 234, 212, 0.25);
    }

    .toast {
      position: fixed;
      left: 50%;
      bottom: 24px;
      z-index: 10;
      padding: 12px 18px;
      border: 1px solid rgba(255, 255, 255, 0.1);
      border-radius: 12px;
      opacity: 0;
      color: var(--text);
      background: #172033;
      box-shadow: 0 10px 35px rgba(0, 0, 0, 0.35);
      transform: translate(-50%, 20px);
      pointer-events: none;
      transition: opacity 0.25s ease, transform 0.25s ease;
    }

    .toast.show {
      opacity: 1;
      transform: translate(-50%, 0);
    }

    @media (max-width: 480px) {
      body {
        padding: 14px;
      }

      .calculator {
        padding: 24px 18px;
        border-radius: 23px;
      }

      .actions {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>

<body>
  <main class="calculator">
    <div class="logo" aria-hidden="true">🍜</div>

    <h1>Bar Sajgon</h1>
    <p class="subtitle">Kalkulator zamówienia</p>

    <div class="price-card">
      <span>Cena za zestaw</span>
      <strong>15 000 $</strong>
    </div>

    <div class="counter">
      <button
        class="counter-button"
        type="button"
        onclick="changeCount(-1)"
        aria-label="Zmniejsz liczbę zestawów"
      >
        -
      </button>

      <span class="count" id="count">0</span>

      <button
        class="counter-button"
        type="button"
        onclick="changeCount(1)"
        aria-label="Zwiększ liczbę zestawów"
      >
        +
      </button>
    </div>

    <label class="input-label" for="quantity">
      Wpisz liczbę zestawów
    </label>

    <input
      class="number-input"
      id="quantity"
      type="number"
      min="0"
      step="1"
      value="0"
      inputmode="numeric"
    >

    <section class="summary" aria-live="polite">
      <div class="summary-label">Do zapłaty</div>
      <div class="total" id="total">0 $</div>
      <div class="selection" id="selection">Wybrano: 0 zestawów</div>
      <div class="discount-info" id="discountInfo">
        Zastosowano rabat 50%
      </div>
    </section>

    <div class="actions">
      <button class="action-button" type="button" onclick="resetCalculator()">
        Wyczyść
      </button>

      <button
        class="action-button primary"
        type="button"
        onclick="copySummary()"
      >
        Kopiuj podsumowanie
      </button>

      <button
        class="action-button"
        id="discountButton"
        type="button"
        onclick="toggleDiscount()"
      >
        Rabat 50%: OFF
      </button>

      <button class="action-button" type="button" onclick="changeTheme()">
        🎨 Zmień motyw
      </button>
    </div>
  </main>

  <div class="toast" id="toast" role="status"></div>

  <script>
    const PRICE = 15000;

    const themes = [
      ["#07111f", "#111c30"],
      ["#1c102d", "#361751"],
      ["#071f1a", "#123a2e"],
      ["#2b0f17", "#4a1925"],
      ["#21160b", "#443018"]
    ];

    const quantityInput = document.getElementById("quantity");
    const countElement = document.getElementById("count");
    const totalElement = document.getElementById("total");
    const selectionElement = document.getElementById("selection");
    const discountInfo = document.getElementById("discountInfo");
    const discountButton = document.getElementById("discountButton");
    const toast = document.getElementById("toast");

    let count = 0;
    let discountEnabled = false;
    let themeIndex = 0;
    let toastTimeout;

    function formatMoney(value) {
      return value.toLocaleString("pl-PL") + " $";
    }

    function getTotal() {
      const subtotal = count * PRICE;
      return discountEnabled ? Math.round(subtotal * 0.5) : subtotal;
    }

    function getSetWord(value) {
      if (value === 1) {
        return "zestaw";
      }

      const lastTwoDigits = value % 100;
      const lastDigit = value % 10;

      if (
        lastDigit >= 2 &&
        lastDigit <= 4 &&
        !(lastTwoDigits >= 12 && lastTwoDigits <= 14)
      ) {
        return "zestawy";
      }

      return "zestawów";
    }

    function updateCalculator() {
      quantityInput.value = count;
      countElement.textContent = count;
      totalElement.textContent = formatMoney(getTotal());

      selectionElement.textContent =
        `Wybrano: ${count} ${getSetWord(count)}`;

      discountInfo.classList.toggle("visible", discountEnabled);
      discountButton.classList.toggle(
        "discount-active",
        discountEnabled
      );

      discountButton.textContent =
        `Rabat 50%: ${discountEnabled ? "ON" : "OFF"}`;
    }

    function changeCount(change) {
      count = Math.max(0, count + change);
      updateCalculator();
    }

    function setCountFromInput() {
      const parsedValue = Number.parseInt(quantityInput.value, 10);
      count = Number.isFinite(parsedValue) ? Math.max(0, parsedValue) : 0;
      updateCalculator();
    }

    function resetCalculator() {
      count = 0;
      discountEnabled = false;
      updateCalculator();
      showToast("Kalkulator został wyczyszczony");
    }

    function toggleDiscount() {
      discountEnabled = !discountEnabled;
      updateCalculator();

      showToast(
        discountEnabled
          ? "Włączono rabat 50%"
          : "Wyłączono rabat"
      );
    }

    function changeTheme() {
      themeIndex = (themeIndex + 1) % themes.length;

      const [firstColor, secondColor] = themes[themeIndex];

      document.documentElement.style.setProperty(
        "--background-1",
        firstColor
      );

      document.documentElement.style.setProperty(
        "--background-2",
        secondColor
      );

      localStorage.setItem("barSajgonTheme", themeIndex);
    }

    async function copySummary() {
      const summary = [
        "Bar Sajgon",
        `Zestawy: ${count}`,
        `Cena za zestaw: ${formatMoney(PRICE)}`,
        `Rabat: ${discountEnabled ? "50%" : "brak"}`,
        `Suma: ${formatMoney(getTotal())}`
      ].join("\n");

      try {
        await navigator.clipboard.writeText(summary);
        showToast("Skopiowano podsumowanie");
      } catch {
        const temporaryInput = document.createElement("textarea");
        temporaryInput.value = summary;
        document.body.appendChild(temporaryInput);
        temporaryInput.select();
        document.execCommand("copy");
        temporaryInput.remove();

        showToast("Skopiowano podsumowanie");
      }
    }

    function showToast(message) {
      clearTimeout(toastTimeout);

      toast.textContent = message;
      toast.classList.add("show");

      toastTimeout = setTimeout(() => {
        toast.classList.remove("show");
      }, 2200);
    }

    quantityInput.addEventListener("input", setCountFromInput);

    quantityInput.addEventListener("keydown", event => {
      if (event.key === "ArrowUp") {
        event.preventDefault();
        changeCount(1);
      }

      if (event.key === "ArrowDown") {
        event.preventDefault();
        changeCount(-1);
      }
    });

    const savedTheme = Number.parseInt(
      localStorage.getItem("barSajgonTheme"),
      10
    );

    if (Number.isInteger(savedTheme) && themes[savedTheme]) {
      themeIndex = savedTheme;

      document.documentElement.style.setProperty(
        "--background-1",
        themes[themeIndex][0]
      );

      document.documentElement.style.setProperty(
        "--background-2",
        themes[themeIndex][1]
      );
    }

    updateCalculator();
  </script>
</body>
</html>

