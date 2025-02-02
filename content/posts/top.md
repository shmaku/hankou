+++
title = "持仓"
date = "2025-02-02"
draft = false
+++

新和成 （002001）  
2024/12/13  
￥21.67

{{ $today := now }}
{{ $previousDate := "2024-12-13" | time.AsTime }}  
{{ $daysDifference := sub (time $today) (time $previousDate) | time.Days }}
{{ $daysDifference | int }}

<!-- 显示结果 -->
持仓 {{ $daysDifference | int }} 天。
