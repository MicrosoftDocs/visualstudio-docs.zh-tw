---
title: HOW TO：設定效能規則 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 243e2311b67c17c91d8c064f6ba66e828df5e86e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928850"
---
# <a name="how-to-configure-performance-rules"></a>HOW TO：設定效能規則
Visual Studio 程式碼剖析工具的效能警告指出，正在進行程式碼剖析的應用程式中發生問題，可能會降低程式執行速度。 警告也可能表示您可能需要變更收集方法，以收集更有用的資料。 在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]中開啟程式碼剖析資料檔案時，效能警告會於程式碼剖析工作階段中自動產生，並出現在 [錯誤清單] 視窗。 某些警告可能不適用於您感興趣的案例，有些則可能是不正確引發的警告。 您可以設定效能警告以顯示或隱藏特定警告。  
  
### <a name="to-configure-profiler-performance-warnings"></a>設定程式碼剖析工具效能警告  
  
1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
2.  展開 [效能工具]，然後按一下 [規則]。  
  
3.  若要啟用或停用警告，請選取或清除警告 [識別碼] 旁邊的核取方塊。  
  
4.  若要指定規則的警告層級，請按一下規則旁的 [動作] 儲存格，然後按一下警告層級。  
  
    -   **已停用** - 停用規則 (這與規則識別碼旁的清除核取方塊相同)。  
  
    -   **警告** - 將規則顯示為警告。  
  
    -   **錯誤** - 中止執行程式碼剖析，並將規則顯示為錯誤。  
  
    -   **資訊** - 僅將規則顯示為資訊。