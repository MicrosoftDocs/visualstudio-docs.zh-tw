---
title: 編輯後繼續錯誤訊息對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b6252fbaf67a9a5b4173c0fee3f65607e9cc462
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227229"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>編輯後繼續錯誤訊息對話方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

支援編輯後繼續 的語言中的偵錯時，會出現此對話方塊，但**編輯後繼續**不適用於您所做的程式碼變更的類型。 方塊內的錯誤訊息會提供更詳細的說明。 出現這個對話方塊的可能原因包括：  
  
-   您嘗試在已啟用 Unmanaged 偵錯時編輯 Managed 程式碼。 [編輯後繼續] 不會處理混合模式偵錯。  
  
-   您嘗試編輯 SQL Server 程式碼。  
  
-   您嘗試在下列項目進行偵錯時編輯程式碼：Dr.Watson 傾印。  
  
-   您嘗試編輯之後，發生未處理例外狀況的程式碼 」 和 「 選項 」**回溯呼叫堆疊上未處理例外狀況**「 未選取。  
  
-   您嘗試在進行內嵌執行階段應用程式偵錯時編輯程式碼。  
  
-   您嘗試編輯而不是從附加至程式中的程式碼**偵錯**功能表。  
  
-   您嘗試編輯最佳化程式碼。  
  
-   您嘗試在目標為 64 位元應用程式時編輯 Managed 程式碼。 如果要使用 [編輯後繼續]，就必須將目標設定為 x86  (*專案***屬性**，**編譯**索引標籤上，**進階編譯器**設定。)。  
  
-   您嘗試在已於偵錯期間修改且已重新載入的組譯碼中編輯程式碼。  
  
-   您嘗試編輯尚未載入之組譯碼中的程式碼。  
  
-   您已開始偵錯舊版的應用程式 (因為新版本有建置錯誤)。  
  
-   您嘗試在程式碼正在執行時編輯該程式碼。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **[確定]**  
 結束對話方塊，並取消緊接在前的編輯嘗試。  
  
## <a name="see-also"></a>另請參閱  
 [支援的程式碼變更 (C++)](../debugger/supported-code-changes-cpp.md)



