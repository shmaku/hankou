+++
title = "持仓"
date = 2025-02-02
draft = false
target_date = "2024-12-13"
+++

新和成 （002001）  
2024/12/13  
￥21.67

{{ $targetDate := .Params.target_date }}  <!-- 获取目标日期 -->
{{ $today := now }}  <!-- 获取今天的日期 -->

<!-- 计算天数差 -->
{{ $targetDateParsed := time $targetDate }}  <!-- 将目标日期字符串转换为时间对象 -->
{{ $diff := $today.Sub $targetDateParsed }}  <!-- 计算日期差 -->
{{ $days := $diff.Hours | div 24 }}  <!-- 获取时间差的小时数并转换为天数 -->

<!-- 显示结果 -->
持仓 {{ $days | printf "%.0f" }} 天。

