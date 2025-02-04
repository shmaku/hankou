+++
title = "持仓"
date = 2025-02-03
draft = false
+++

新和成 （002001）  
2024/12/13  
￥21.67
最新价格：<span id="stockPrice"></span>
持仓 <span id="daysDifference"></span> 天……

<script>
    const today = new Date();
    const previousDate = new Date('2024-12-13'); // 这里假设之前某日是2024年12月13日
    const oneDay = 24 * 60 * 60 * 1000; // hours * minutes * seconds * milliseconds
    const diffDays = Math.round(Math.abs((today - previousDate) / oneDay));
    document.getElementById('daysDifference').innerText = diffDays;
</script>

 <script>
        async function getStockPrice() {
            const apiKey = 'U31XQFWRL9AC1J4Z';  // 使用有效的API密钥
            const symbol = '002001.SZ';  // 股票代码已加引号
            const url = `https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol=${symbol}&outputsize=full&apikey=${apiKey}`;
            
            try {
                const response = await fetch(url);
                const data = await response.json();
                
                if (data["Time Series (Daily)"]) {
                    // 获取最近的时间和价格
                    const latestTime = Object.keys(data["Time Series (Daily)"])[0];
                    const latestData = data["Time Series (Daily)"][latestTime];
                    const price = latestData["4. close"];

                    // 将价格保留两位小数
                    const formattedPrice = parseFloat(price).toFixed(2);
                    document.getElementById('stockPrice').innerText = `￥${formattedPrice}`;

                }
                }
    </script>