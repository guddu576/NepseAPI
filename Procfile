<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NEPSE Indices, Sub-indices, Companies & Market Summary Assistant</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 0; padding: 0; background: #f4f4f9; }
        .container { width: 80%; margin: 50px auto; background: #fff; padding: 20px; border-radius: 10px; box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); }
        #indicesSection, #subIndicesSection, #companiesSection, #marketSummarySection { margin-bottom: 30px; }
        .index, .subIndex, .company, .marketSummary { padding: 10px; border: 1px solid #ccc; margin: 5px 0; border-radius: 5px; background: #f9f9f9; }
        #chatSection { margin-top: 30px; }
        #chatMessages { height: 300px; overflow-y: auto; border: 1px solid #ccc; padding: 10px; background: #f9f9f9; margin-bottom: 10px; }
        #chatInput { width: calc(100% - 120px); padding: 10px; border: 1px solid #ccc; border-radius: 5px; }
        button { padding: 10px 20px; background-color: #007bff; color: white; border: none; border-radius: 5px; cursor: pointer; }
        button:hover { background-color: #0056b3; }
    </style>
</head>
<body>
    <div class="container">
        <h1>NEPSE Indices, Sub-indices, Companies & Market Summary Assistant</h1>

        <!-- Indices Section -->
        <div id="indicesSection">
            <h3>Market Indices</h3>
            <div class="index">NEPSE Index: <strong id="nepseIndex">Loading...</strong></div>
            <div class="index">Float Index: <strong id="floatIndex">Loading...</strong></div>
            <div class="index">Sensitive Index: <strong id="sensitiveIndex">Loading...</strong></div>
            <button onclick="refreshIndices()">Refresh Indices</button>
        </div>

        <!-- Sub-indices Section -->
        <div id="subIndicesSection">
            <h3>Sub-indices</h3>
            <div class="subIndex">Banking Index: <strong id="bankingIndex">Loading...</strong></div>
            <div class="subIndex">Development Bank Index: <strong id="devBankIndex">Loading...</strong></div>
            <div class="subIndex">Hydropower Index: <strong id="hydropowerIndex">Loading...</strong></div>
            <button onclick="refreshSubIndices()">Refresh Sub-indices</button>
        </div>

        <!-- Companies Section -->
        <div id="companiesSection">
            <h3>Company Details</h3>
            <div class="company">Company: <strong>ABC Bank</strong> - Price: <strong id="abcPrice">Loading...</strong></div>
            <div class="company">Company: <strong>XYZ Cement</strong> - Price: <strong id="xyzPrice">Loading...</strong></div>
            <div class="company">Company: <strong>PQR Energy</strong> - Price: <strong id="pqrPrice">Loading...</strong></div>
            <button onclick="refreshCompanies()">Refresh Prices</button>
        </div>

        <!-- Market Summary Section -->
        <div id="marketSummarySection">
            <h3>Market Summary</h3>
            <div class="marketSummary">Total Market Capitalization: <strong id="marketCap">Loading...</strong></div>
            <div class="marketSummary">Total Traded Volume: <strong id="tradedVolume">Loading...</strong></div>
            <div class="marketSummary">Total Traded Value: <strong id="tradedValue">Loading...</strong></div>
            <div class="marketSummary">Top Gainers: <strong id="topGainers">Loading...</strong></div>
            <div class="marketSummary">Top Losers: <strong id="topLosers">Loading...</strong></div>
            <div class="marketSummary">Market Trend: <strong id="marketTrend">Loading...</strong></div>
            <button onclick="refreshMarketSummary()">Refresh Market Summary</button>
        </div>

        <!-- Chat Section -->
        <div id="chatSection">
            <h3>Chat with NEPSE Assistant</h3>
            <div id="chatMessages"></div>
            <div style="display: flex;">
                <input type="text" id="chatInput" placeholder="Ask about indices, sub-indices, companies, or market summary..." />
                <button onclick="handleChat()">Send</button>
            </div>
        </div>
    </div>

    <script>
        // Mock Data
        let nepseIndex = 2000.15;
        let floatIndex = 800.32;
        let sensitiveIndex = 1000.54;
        let subIndices = {
            Banking: 950.75,
            DevBank: 580.45,
            Hydropower: 720.80
        };
        let companyPrices = {
            ABC: 350.75,
            XYZ: 550.25,
            PQR: 725.60
        };
        let marketSummary = {
            marketCap: 15000000000, // Example market cap in NPR
            tradedVolume: 1200000, // Example traded volume (number of shares)
            tradedValue: 5000000000, // Example total value of trades in NPR
            topGainers: "ABC Bank (+2.5%), XYZ Cement (+1.8%)",
            topLosers: "PQR Energy (-1.2%), XYZ Cement (-0.5%)",
            marketTrend: "Up (1.2%)"
        };
        let lastUpdated = new Date();

        // Display indices
        function displayIndices() {
            document.getElementById('nepseIndex').textContent = nepseIndex.toFixed(2);
            document.getElementById('floatIndex').textContent = floatIndex.toFixed(2);
            document.getElementById('sensitiveIndex').textContent = sensitiveIndex.toFixed(2);
        }

        // Display sub-indices
        function displaySubIndices() {
            document.getElementById('bankingIndex').textContent = subIndices.Banking.toFixed(2);
            document.getElementById('devBankIndex').textContent = subIndices.DevBank.toFixed(2);
            document.getElementById('hydropowerIndex').textContent = subIndices.Hydropower.toFixed(2);
        }

        // Display company prices
        function displayCompanyPrices() {
            document.getElementById('abcPrice').textContent = companyPrices.ABC.toFixed(2);
            document.getElementById('xyzPrice').textContent = companyPrices.XYZ.toFixed(2);
            document.getElementById('pqrPrice').textContent = companyPrices.PQR.toFixed(2);
        }

        // Display market summary
        function displayMarketSummary() {
            document.getElementById('marketCap').textContent = marketSummary.marketCap.toLocaleString();
            document.getElementById('tradedVolume').textContent = marketSummary.tradedVolume.toLocaleString();
            document.getElementById('tradedValue').textContent = marketSummary.tradedValue.toLocaleString();
            document.getElementById('topGainers').textContent = marketSummary.topGainers;
            document.getElementById('topLosers').textContent = marketSummary.topLosers;
            document.getElementById('marketTrend').textContent = marketSummary.marketTrend;
        }

        // Refresh indices (Simulated random updates)
        function refreshIndices() {
            nepseIndex += (Math.random() * 10 - 5);
            floatIndex += (Math.random() * 5 - 2.5);
            sensitiveIndex += (Math.random() * 7 - 3.5);
            lastUpdated = new Date();
            displayIndices();
        }

        // Refresh sub-indices (Simulated random updates)
        function refreshSubIndices() {
            subIndices.Banking += (Math.random() * 20 - 10);
            subIndices.DevBank += (Math.random() * 15 - 7.5);
            subIndices.Hydropower += (Math.random() * 25 - 12.5);
            lastUpdated = new Date();
            displaySubIndices();
        }

        // Refresh company prices (Simulated random updates)
        function refreshCompanies() {
            companyPrices.ABC += (Math.random() * 20 - 10);
            companyPrices.XYZ += (Math.random() * 15 - 7.5);
            companyPrices.PQR += (Math.random() * 25 - 12.5);
            lastUpdated = new Date();
            displayCompanyPrices();
        }

        // Refresh market summary (Simulated random updates)
        function refreshMarketSummary() {
            marketSummary.marketCap += (Math.random() * 100000000 - 50000000); // Random update
            marketSummary.tradedVolume += (Math.random() * 50000 - 25000); // Random update
            marketSummary.tradedValue += (Math.random() * 100000000 - 50000000); // Random update
            lastUpdated = new Date();
            displayMarketSummary();
        }

        // Chat functionality
        function handleChat() {
            const chatInput = document.getElementById('chatInput');
            const chatMessages = document.getElementById('chatMessages');
            const userMessage = chatInput.value.trim();

            if (!userMessage) return;

            // Display user's message
            chatMessages.innerHTML += `<div><strong>You:</strong> ${userMessage}</div>`;
            chatInput.value = "";

            // Process bot response
            let botResponse = "I'm sorry, I didn't understand that.";
            if (userMessage.toLowerCase().includes("nepse index")) {
                botResponse = `The NEPSE index is currently ${nepseIndex.toFixed(2)} as of ${lastUpdated.toLocaleString()}.`;
            } else if (userMessage.toLowerCase().includes("float index")) {
                botResponse = `The Float index is currently ${floatIndex.toFixed(2)} as of ${lastUpdated.toLocaleString()}.`;
            } else if (userMessage.toLowerCase().includes("sensitive index")) {
                botResponse = `The Sensitive index is currently ${sensitiveIndex.toFixed(2)} as of ${lastUpdated.toLocaleString()}.`;
            } else if (userMessage.toLowerCase().includes("market summary")) {
                botResponse = `
                    Market Summary:
                    <ul>
                        <li>Total Market Capitalization: NPR ${marketSummary.marketCap.toLocaleString()}</li>
                        <li>Total Traded Volume: ${marketSummary.tradedVolume.toLocaleString()} shares</li>
                        <li>Total Traded Value: NPR ${marketSummary.tradedValue.toLocaleString()}</li>
                        <li>Top Gainers: ${marketSummary.topGainers}</li>
                        <li>Top Losers: ${marketSummary.topLosers}</li>
                        <li>Market Trend: ${marketSummary.marketTrend}</li>
                    </ul>
                `;
            }

            // Display bot's response
            chatMessages.innerHTML += `<div><strong>Bot:</strong> ${botResponse}</div>`;
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }

        // Initialize
        displayIndices();
        displaySubIndices();
        displayCompanyPrices();
        displayMarketSummary();
    </script>
</body>
</html>web: gunicorn apinepse.wsgi:application --log-file -
