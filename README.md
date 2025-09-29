# co7<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>My Courier Delivery & Ride Booking</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: white;
      color: #333;
    }
    header {
      background: #87ceeb; /* sky blue */
      color: white;
      padding: 1rem;
      text-align: center;
      font-size: 1.2rem;
      font-weight: bold;
    }
    .container {
      max-width: 900px;
      margin: 2rem auto;
      padding: 1rem;
      border: 1px solid #87ceeb;
      border-radius: 8px;
    }
    .tabs {
      display: flex;
      justify-content: space-around;
      margin-bottom: 1rem;
    }
    button {
      padding: 0.5rem 1rem;
      background: white;
      border: 2px solid #87ceeb;
      border-radius: 4px;
      cursor: pointer;
      color: #87ceeb;
      font-weight: bold;
      transition: background-color 0.3s, color 0.3s;
    }
    button.active, button:hover {
      background: #87ceeb;
      color: white;
    }
    .section {
      display: none;
      margin-top: 1rem;
      border-top: 1px solid #87ceeb;
      padding-top: 1rem;
    }
    .section.active {
      display: block;
    }
    label {
      display: block;
      margin: 0.75rem 0 0.25rem;
      font-weight: bold;
    }
    select, input[type="radio"] {
      margin-right: 0.5rem;
    }
    .vehicle-options label {
      display: inline-block;
      margin-right: 1rem;
      font-weight: normal;
    }
  </style>
</head>
<body>
  <header>
    Add Display Banner Here
  </header>
  <div class="container">
    <div class="tabs">
      <button id="courierBtn" class="active">Courier</button>
      <button id="rideBtn">Ride Booking</button>
      <button id="rentBtn">Rental Vehicle</button>
    </div>

    <!-- Courier Section -->
    <div id="courier" class="section active">
      <label>Choose Location:</label>
      <select id="courierLocation">
        <option value="send">Send</option>
        <option value="receive">Receive</option>
      </select>

      <label>Vehicle Type:</label>
      <div class="vehicle-options">
        <label><input type="radio" name="courierVehicle" value="bike" checked /> Bike</label>
        <label><input type="radio" name="courierVehicle" value="auto" /> Auto</label>
        <label><input type="radio" name="courierVehicle" value="car" /> Car</label>
        <label><input type="radio" name="courierVehicle" value="miniauto" /> Mini Auto</label>
        <label><input type="radio" name="courierVehicle" value="lorry" /> Lorry</label>
      </div>
    </div>

    <!-- Ride Booking Section -->
    <div id="ride" class="section">
      <label>Select Ride Type:</label>
      <div class="vehicle-options">
        <label><input type="radio" name="rideType" value="bike" checked /> Bike</label>
        <label><input type="radio" name="rideType" value="auto" /> Auto</label>
        <label><input type="radio" name="rideType" value="car" /> Car</label>
      </div>
    </div>

    <!-- Rental Vehicle Section -->
    <div id="rent" class="section">
      <label>Select Mode:</label>
      <div class="vehicle-options">
        <label><input type="radio" name="rentMode" value="self" checked /> Self</label>
        <label><input type="radio" name="rentMode" value="driver" /> With Driver</label>
      </div>

      <div id="selfVehicleOptions">
        <label>Choose Vehicle:</label>
        <div class="vehicle-options">
          <label><input type="radio" name="selfVehicle" value="bike" checked /> Bike</label>
          <label><input type="radio" name="selfVehicle" value="car" /> Car</label>
          <label><input type="radio" name="selfVehicle" value="auto" /> Auto</label>
        </div>
      </div>

      <div id="driverVehicleOptions" style="display:none;">
        <label>Choose Vehicle:</label>
        <div class="vehicle-options">
          <label><input type="radio" name="driverVehicle" value="bike" /> Bike</label>
          <label><input type="radio" name="driverVehicle" value="car" /> Car</label>
          <label><input type="radio" name="driverVehicle" value="auto" /> Auto</label>
          <label><input type="radio" name="driverVehicle" value="bolero" /> Bolero</label>
          <label><input type="radio" name="driverVehicle" value="volvo" /> Volvo</label>
          <label><input type="radio" name="driverVehicle" value="jeep" /> Jeep</label>
        </div>
      </div>
    </div>
  </div>

  <script>
    // Tabs switching
    const courierBtn = document.getElementById('courierBtn');
    const rideBtn = document.getElementById('rideBtn');
    const rentBtn = document.getElementById('rentBtn');
    const courierSection = document.getElementById('courier');
    const rideSection = document.getElementById('ride');
    const rentSection = document.getElementById('rent');

    courierBtn.addEventListener('click', () => {
      courierBtn.classList.add('active');
      rideBtn.classList.remove('active');
      rentBtn.classList.remove('active');
      courierSection.classList.add('active');
      rideSection.classList.remove('active');
      rentSection.classList.remove('active');
    });

    rideBtn.addEventListener('click', () => {
      rideBtn.classList.add('active');
      courierBtn.classList.remove('active');
      rentBtn.classList.remove('active');
      rideSection.classList.add('active');
      courierSection.classList.remove('active');
      rentSection.classList.remove('active');
    });

    rentBtn.addEventListener('click', () => {
      rentBtn.classList.add('active');
      rideBtn.classList.remove('active');
      courierBtn.classList.remove('active');
      rentSection.classList.add('active');
      rideSection.classList.remove('active');
      courierSection.classList.remove('active');
    });

    // Rental vehicle mode toggle
    const rentModeRadios = document.getElementsByName('rentMode');
    const selfVehicleOptions = document.getElementById('selfVehicleOptions');
    const driverVehicleOptions = document.getElementById('driverVehicleOptions');

    rentModeRadios.forEach(radio => {
      radio.addEventListener('change', () => {
        if (radio.value === 'self') {
          selfVehicleOptions.style.display = 'block';
          driverVehicleOptions.style.display = 'none';
        } else {
          selfVehicleOptions.style.display = 'none';
          driverVehicleOptions.style.display = 'block';
        }
      });
    });
  </script>
</body>
</html>
