<!DOCTYPE html>
<html lang="or">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Loan Details</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Arial, sans-serif;
    }
    body {
      background: #f0f2f5;
      color: #333;
      padding: 10px;
    }
    .app-card {
      max-width: 1080px;
      margin: 0 auto;
      background: #ffffff;
      border-radius: 8px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      overflow: hidden;
    }
    
    /* Header */
    .title-banner {
      background: #FCE4D6;
      padding: 14px;
      text-align: center;
      font-size: 22px;
      font-weight: bold;
      letter-spacing: 1px;
      color: #111;
      border-bottom: 2px solid #e2c0b0;
    }

    /* Form Section */
    .entry-area {
      background: #fdfdfd;
      padding: 15px;
      border-bottom: 1px solid #ddd;
    }
    .form-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 10px;
      align-items: end;
    }
    .input-box {
      display: flex;
      flex-direction: column;
    }
    .input-box label {
      font-size: 12px;
      font-weight: bold;
      margin-bottom: 4px;
      color: #444;
    }
    .input-box input, .input-box select {
      padding: 8px 10px;
      border: 1px solid #bbb;
      border-radius: 5px;
      font-size: 13px;
      outline: none;
    }
    .input-box input:focus, .input-box select:focus {
      border-color: #28a745;
    }

    /* Action Buttons */
    .btn-controls {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      margin-top: 14px;
    }
    button {
      padding: 8px 16px;
      border: none;
      border-radius: 5px;
      font-size: 13px;
      font-weight: bold;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }
    .btn-add {
      background: #28a745;
      color: #fff;
    }
    .btn-add:hover { background: #218838; }
    .btn-pdf {
      background: #d9534f;
      color: #fff;
    }
    .btn-pdf:hover { background: #c9302c; }
    .btn-reset {
      background: #6c757d;
      color: #fff;
    }
    .btn-reset:hover { background: #5a6268; }
    .btn-del {
      background: #ff4d4f;
      color: #fff;
      padding: 4px 8px;
      font-size: 11px;
      border-radius: 4px;
    }

    /* Content Layout */
    .data-container {
      display: flex;
      flex-direction: row;
      gap: 15px;
      padding: 15px;
      flex-wrap: wrap;
    }
    .table-left {
      flex: 2;
      min-width: 550px;
      overflow-x: auto;
    }
    .table-right {
      flex: 1;
      min-width: 270px;
    }

    /* Tables */
    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 13px;
    }
    th {
      background: #FFF200;
      color: #000080;
      padding: 9px 6px;
      border: 1px solid #ccc;
      font-weight: bold;
      text-align: center;
    }
    td {
      padding: 8px 6px;
      border: 1px solid #e2e2e2;
      text-align: center;
    }
    tr:nth-child(even) { background: #fafafa; }
    tr:hover { background: #f1f8ff; }
    .num-align {
      text-align: right;
      padding-right: 10px;
    }

    /* Summary Specific Styling */
    .total-header td {
      background: #1B4D1B;
      color: #ffffff;
      font-weight: bold;
      font-size: 14px;
      text-align: center;
    }
    .total-header td.num-align {
      background: #ffffff;
      color: #000000;
      border: 2px solid #1B4D1B;
    }
    .bal-header td {
      background: #FFFF00;
      color: #000080;
      font-weight: bold;
      font-size: 14px;
      text-align: center;
    }
    .bal-header td.num-align {
      background: #ffffff;
      color: #c00000;
      font-weight: bold;
      border: 2px solid #ffd700;
    }

    /* Print Preview */
    @media print {
      body { background: #fff; padding: 0; }
      .app-card { box-shadow: none; border-radius: 0; width: 100%; }
      .entry-area, .btn-controls, .btn-del, th.action-hide, td.action-hide { display: none !important; }
      .title-banner { font-size: 18px; padding: 10px; -webkit-print-color-adjust: exact; print-color-adjust: exact; }
      th, .total-header td, .bal-header td { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
    }
  </style>
</head>
<body>

<div class="app-card">
  <div class="title-banner">MY LOAN DETAILS</div>

  <!-- Entry Form Area -->
  <div class="entry-area">
    <div class="form-grid">
      <div class="input-box">
        <label>PAYMENT DATE 📅</label>
        <input type="date" id="pDate">
      </div>
      <div class="input-box">
        <label>LOAN BANK 🏦</label>
        <select id="lBank">
          <option value="KOTAK BANK">KOTAK BANK 🏦</option>
          <option value="SBI BANK">SBI BANK 🏦</option>
          <option value="SBI CARD">SBI CARD ♠</option>
          <option value="HDFC BANK">HDFC BANK 🏦</option>
          <option value="ICICI BANK">ICICI BANK 🏦</option>
          <option value="OTHER">OTHER BANK</option>
        </select>
      </div>
      <div class="input-box">
        <label>TOTAL CASH 💰 (₹)</label>
        <input type="number" id="totCash" placeholder="eg. 15736">
      </div>
      <div class="input-box">
        <label>PAID DATE 📅 (Optional)</label>
        <input type="date" id="paidDate">
      </div>
      <div class="input-box">
        <label>PAID 💰 (₹)</label>
        <input type="number" id="paidCash" placeholder="eg. 15736">
      </div>
      <button class="btn-add" onclick="addNewEntry()">➕ Add Entry</button>
    </div>

    <div class="btn-controls">
      <button class="btn-pdf" onclick="window.print()">🖨️ Print / Save PDF</button>
      <button class="btn-reset" onclick="resetAllData()">🔄 Reset Data</button>
    </div>
  </div>

  <!-- Data Display Tables -->
  <div class="data-container">
    <!-- Transactions Table -->
    <div class="table-left">
      <table>
        <thead>
          <tr>
            <th>PAYMENT DATE 📅</th>
            <th>LOAN BANK 🏦</th>
            <th>TOTAL CASH 💰</th>
            <th>PAID DATE 📅</th>
            <th>PAID 💰</th>
            <th class="action-hide">ACTION</th>
          </tr>
        </thead>
        <tbody id="loanRows"></tbody>
      </table>
    </div>

    <!-- Right Summary Table -->
    <div class="table-right">
      <table>
        <thead>
          <tr>
            <th>LOAN BANK 🏦</th>
            <th>TOTAL CASH 💰</th>
          </tr>
        </thead>
        <tbody id="bankSummaryRows"></tbody>
        <tfoot>
          <tr class="total-header">
            <td>Total Amount</td>
            <td class="num-align" id="totalAmountText">₹0</td>
          </tr>
          <tr class="bal-header">
            <td>BALANCE ⚖️</td>
            <td class="num-align" id="balAmountText">₹0</td>
          </tr>
        </tfoot>
      </table>
    </div>
  </div>
</div>

<script>
  // Sample seed data
  const defaultList = [
    { pDate: "2026-01-02", bank: "KOTAK BANK", totalCash: 15736, paidDate: "2026-09-02", paid: 15736 },
    { pDate: "2026-09-03", bank: "SBI BANK", totalCash: 3120, paidDate: "2026-09-03", paid: 3120 },
    { pDate: "2026-09-05", bank: "SBI BANK", totalCash: 15693, paidDate: "2026-09-05", paid: 15693 },
    { pDate: "2026-09-05", bank: "SBI BANK", totalCash: 7554, paidDate: "2026-09-05", paid: 7554 },
    { pDate: "2026-09-05", bank: "KOTAK BANK", totalCash: 4742, paidDate: "2026-09-05", paid: 4742 },
    { pDate: "2026-09-15", bank: "KOTAK BANK", totalCash: 12463, paidDate: "2026-09-15", paid: 0 },
    { pDate: "2026-09-24", bank: "SBI CARD", totalCash: 6723, paidDate: "2026-09-24", paid: 0 }
  ];

  let myLoans = JSON.parse(localStorage.getItem('my_loans_v2')) || defaultList;

  function showDate(dateStr) {
    if (!dateStr) return "-";
    const parts = dateStr.split("-");
    if (parts.length === 3) {
      return `${parts[2]}/${parts[1]}/${parts[0]}`;
    }
    return dateStr;
  }

  function updateDisplay() {
    const tbody = document.getElementById('loanRows');
    tbody.innerHTML = '';

    let totalCashSum = 0;
    let totalPaidSum = 0;
    const bankGroups = {};

    myLoans.forEach((row, i) => {
      const tc = Number(row.totalCash) || 0;
      const pd = Number(row.paid) || 0;

      totalCashSum += tc;
      totalPaidSum += pd;

      bankGroups[row.bank] = (bankGroups[row.bank] || 0) + tc;

      const tr = document.createElement('tr');
      tr.innerHTML = `
        <td>${showDate(row.pDate)}</td>
        <td style="text-align: left; padding-left: 10px;">${row.bank}</td>
        <td class="num-align">${tc.toLocaleString('en-IN')}</td>
        <td>${pd > 0 ? showDate(row.paidDate) : '-'}</td>
        <td class="num-align">${pd > 0 ? pd.toLocaleString('en-IN') : '-'}</td>
        <td class="action-hide"><button class="btn-del" onclick="removeEntry(${i})">🗑️ Delete</button></td>
      `;
      tbody.appendChild(tr);
    });

    // Summary calculation
    const summaryTbody = document.getElementById('bankSummaryRows');
    summaryTbody.innerHTML = '';

    const baseBanks = ["KOTAK BANK", "SBI BANK", "SBI CARD"];
    baseBanks.forEach(b => {
      if (!bankGroups.hasOwnProperty(b)) bankGroups[b] = 0;
    });

    for (let b in bankGroups) {
      const sTr = document.createElement('tr');
      sTr.innerHTML = `
        <td style="text-align: left; padding-left: 10px;">${b}</td>
        <td class="num-align">${bankGroups[b].toLocaleString('en-IN')}</td>
      `;
      summaryTbody.appendChild(sTr);
    }

    const netBalance = totalCashSum - totalPaidSum;
    document.getElementById('totalAmountText').innerText = '₹' + totalCashSum.toLocaleString('en-IN');
    document.getElementById('balAmountText').innerText = '₹' + netBalance.toLocaleString('en-IN');

    // Save state
    localStorage.setItem('my_loans_v2', JSON.stringify(myLoans));
  }

  function addNewEntry() {
    const pDate = document.getElementById('pDate').value;
    const bank = document.getElementById('lBank').value;
    const totCash = document.getElementById('totCash').value;
    const paidDate = document.getElementById('paidDate').value;
    const paidCash = document.getElementById('paidCash').value || 0;

    if (!totCash) {
      alert("ଦୟାକରି Total Cash ଟଙ୍କା ଲେଖନ୍ତୁ!");
      return;
    }

    myLoans.push({
      pDate: pDate || new Date().toISOString().split('T')[0],
      bank: bank,
      totalCash: Number(totCash),
      paidDate: paidDate || (paidCash > 0 ? pDate : ""),
      paid: Number(paidCash)
    });

    document.getElementById('totCash').value = '';
    document.getElementById('paidCash').value = '';

    updateDisplay();
  }

  function removeEntry(index) {
    if (confirm("ଏହି ଏଣ୍ଟ୍ରିଟି Delete କରିବାକୁ ଚାହୁଁଛନ୍ତି କି?")) {
      myLoans.splice(index, 1);
      updateDisplay();
    }
  }

  function resetAllData() {
    if (confirm("ଡାଟା ରିସେଟ୍ କରିବାକୁ ଚାହୁଁଛନ୍ତି କି?")) {
      myLoans = JSON.parse(JSON.stringify(defaultList));
      updateDisplay();
    }
  }

  // Set default current date
  document.getElementById('pDate').value = new Date().toISOString().split('T')[0];
  document.getElementById('paidDate').value = new Date().toISOString().split('T')[0];

  updateDisplay();
</script>
</body>
</html>
