---
title: Visual Studio for Mac 疑難排解
description: Visual Studio for Mac 使用者的常見問題及解決方法。
ms.topic: troubleshooting
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: a802bf950b5f759a41f88fb9260449fadcea8974
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="troubleshooting"></a>疑難排解

## <a name="viewing-logs-in-visual-studio-for-mac"></a>在 Visual Studio for Mac 中檢視記錄

瀏覽至 [說明] > [開啟記錄目錄] 功能表項目，即可以找到記錄，如下所示：

![開啟記錄目錄功能表項目](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>檢視例外狀況

攔截到例外狀況時，會出現例外狀況泡泡。 若要檢視更多詳細資料，請選取 [檢視詳細資料] 按鈕：

![檢視例外狀況的其他詳細資料](media/troubleshooting-image2.png)

這會顯示 [顯示詳細資料] 對話方塊，以提供例外狀況的詳細資訊：

![](media/troubleshooting-image3.png)

下面詳述對話方塊中如上所編號的重要區段：

1. 例外狀況類型，以顯示所觀察之例外狀況類型的完整名稱。
2. 例外狀況訊息，以顯示例外狀況物件的 [訊息] 屬性值。
3. 內部例外狀況類型，以顯示內部例外狀況樹狀檢視中目前所選取例外狀況之例外狀況類型的完整名稱。
4. 內部例外狀況訊息，以顯示內部例外狀況樹狀檢視中所選取例外狀況的 [訊息] 屬性值。
5. 堆疊追蹤檢視。 這可以透過公開揭示箭號進行摺疊，並包含堆疊框架項目。
6. 非使用者程式碼項目範例。
7. 使用者程式碼項目範例。
8. 屬性檢視，以顯示例外狀況的所有屬性和欄位。 這可以透過公開揭示箭號進行摺疊。
9. 內部例外狀況樹狀檢視。 透過鍵盤向上/向下鍵，或者使用滑鼠或軌跡板，在這個檢視中選取內部例外狀況。
10. 根據預設，這會設定為偵錯工具設定中的 [Debug project code only] (只偵錯專案程式碼) 選項所設定為的項目。 選取此方塊會將所有非使用者程式碼摺疊成堆疊追蹤中的一行。
11. 將 `exception.ToString()` 輸出複製至剪貼簿的 [複製] 按鈕。

請注意，只有在例外狀況有內部例外狀況時，才會顯示其中一些區段。