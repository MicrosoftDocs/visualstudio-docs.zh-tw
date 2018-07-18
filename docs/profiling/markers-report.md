---
title: 標記報告 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b46cb18e1972d22010ce356f1d9208f391f6d79
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31580404"
---
# <a name="markers-report"></a>標記報告
標記報告會列出所顯示時間範圍內的標記。  移動瀏覽、縮放或隱藏通道可能會造成標記顯示或消失。 報表包含每個標記的下列資訊：  
  
-   相對於開始追蹤的開始時間。  
  
-   時間長度。 旗標和訊息的時間長度為零，因為它們表示一瞬間。  
  
-   產生標記的執行緒識別碼。  
  
-   產生標記的 Windows 事件追蹤 (ETW) 提供者。  
  
-   撰寫標記的標記系列。  
  
-   標記所屬的事件分類。  
  
-   標記的重要性層級。  
  
-   標記的類型 (範圍、旗標或訊息)。  
  
-   標記所表示意義的高階描述  
  
 選擇 [匯出] 按鈕來將標記報表儲存為 CSV 檔案。 您可以搭配其他 App 或工具使用 CSV 檔案中的資料。  
  
> [!NOTE]
>  標記報表可以顯示 1,000 個標記。 若要查看所有標記，請將完整的報表匯出成 CSV 檔案。