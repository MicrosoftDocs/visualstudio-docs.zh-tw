---
title: 如何：收集程式行層級取樣資料 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65890bf31a1257c3a41bc1fd7ed3f732c50eda14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185948"
---
# <a name="how-to-collect-line-level-sampling-data"></a>如何：收集程式行層級取樣資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

程式行層級取樣是程式碼剖析工具的一項功能，可以在需要大量處理器資源的函式 (例如包含大量專有樣本的函式) 中判斷處理器花最多時間處理的程式碼。  
  
## <a name="overview"></a>概觀  
 針對程式行層級取樣，程式碼剖析工具會以設定的間隔瀏覽程式呼叫堆疊，並彙總這些結果。 這些結果會顯示取樣時處理器執行的指令。 接著分析與專有樣本有關的收集資料，以找出程式碼和指令指標 (IP)。  
  
 程式行層級取樣適用於 managed 與機器碼。 顯示此資料的效能報告包含 [程式行] 檢視和 [模組] 檢視。  
  
 字元開頭/結尾資訊不適用於機器碼。 對於多行陳述式，行開頭資訊不適用於機器碼；僅行結尾資訊適用。  
  
### <a name="available-data"></a>可用的資料  
 可用的程式行層級取樣資料包含下列資訊︰  
  
- 函式名稱。  
  
- 函式位址。  
  
- 行開頭 – 取樣程式碼的行號。  
  
- 行結尾 – 結束原始程式碼行號。 這通常與「行開頭」資料相同，除非單一程式陳述式跨越多個原始程式碼行。  
  
- 字元開頭 – 彙總樣本開頭的資料行。 這通常是 0，除非一行包含多個程式陳述式。  
  
- 字元結尾 – 彙總樣本結尾的資料行。  
  
- IP - 取得彙總樣本的位址 (僅限 IP 檢視)。  
  
  在 [模組]**** 檢視中，如果函式包含程式行層級統計資料，統計資料會巢狀於每個函式之下。 此外，巢狀於每一行之下的 IP 層級統計資料也會顯示。  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>關閉 Managed 程式碼的程式行層級取樣  
 程式行層級取樣預設為開啟。 您可以執行下列其中一項動作以關閉 Managed 程式碼的程式行層級資料收集︰  
  
- 在進行程式碼剖析之前，輸入 **VSPerfCLREnv /samplelineoff**。 這會影響應用程式和服務。  
  
     — 或者—  
  
- 啟動應用程式時，輸入 **>vsperfcmd/lineoff \<other arguments> **。  
  
## <a name="see-also"></a>另請參閱  
 [設定效能會話](../profiling/configuring-performance-sessions.md)   
 [分析效能工具資料](../profiling/analyzing-performance-tools-data.md)
