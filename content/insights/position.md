+++
title = "Positions"
date = 2024-12-13
author = "Acj"
description = 'The purpose of trading is to make a profit'
+++
"**All trading actions must be justified and can be adjusted.**"<br>

NHU (002001) <br> 
Purchase date：2024-12-13<br>  
Average Purchase Price：￥21.77 <br>
Closing Price of the Previous Trading Day：<span id="stockPrice"></span> <br> 
Positions: <span id="daysDifference"></span> days

<script>
    const today = new Date();
    const previousDate = new Date('2024-12-13'); // 这里假设之前某日是2024年12月13日
    const oneDay = 24 * 60 * 60 * 1000; // hours * minutes * seconds * milliseconds
    const diffDays = Math.round(Math.abs((today - previousDate) / oneDay));
    document.getElementById('daysDifference').innerText = diffDays;
</script>

<script>
    async function getStockPrice() {
        const apiKey = 'U31XQFWRL9AC1J4Z';  // 请替换为有效的API密钥
        const symbol = '002001.SHZ';  
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

                // 显示最新的价格
                document.getElementById('stockPrice').innerText = `￥${formattedPrice}`;
            } else {
                document.getElementById('stockPrice').innerText = '获取价格失败，请检查API调用或股票代码是否正确。';
            }
        } catch (error) {
            document.getElementById('stockPrice').innerText = '请求失败，出现错误。';
        }
    }

    // 页面加载时获取股票价格
    window.onload = getStockPrice;
</script>
