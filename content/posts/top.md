+++
title = '持仓'
date = 2025-02-02
draft = false
target_date: '2024-12-13' 
+++

新和成 （002001）
2024/12/13
￥21.67

{{ $targetDate := .Params.target_date }}  <!-- 获取目标日期 -->
{{ $today := now }}  <!-- 获取今天的日期 -->
{{ $dateFormat := "2006-01-02" }}  <!-- 日期格式 -->

<!-- 计算天数差 -->
{{ $diff := sub (time $today) (time $targetDate) }}
{{ $days := div (float64 $diff) 86400 }}  <!-- 86400 是一天的秒数 -->

<!-- 显示结果 -->
持仓 {{ $days | printf "%.0f" }} 天。