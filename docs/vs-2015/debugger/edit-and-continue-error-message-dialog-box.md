---
title: 編輯後繼續錯誤訊息對話方塊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5437ef982309ef8595f08283f2685e93d346e764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428275"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>編輯後繼續錯誤訊息對話方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您使用支援 [編輯後繼續] 的語言進行偵錯工具時，會出現此對話方塊，但您所做的程式碼變更類型無法使用 [ **編輯後繼續** ]。 方塊內的錯誤訊息會提供更詳細的說明。 出現這個對話方塊的可能原因包括：  
  
- 您嘗試在已啟用 Unmanaged 偵錯時編輯 Managed 程式碼。 [編輯後繼續] 不會處理混合模式偵錯。  
  
- 您嘗試編輯 SQL Server 程式碼。  
  
- 您嘗試在偵測 Dr. Watson 傾印時編輯程式碼。  
  
- 您嘗試在發生未處理的例外狀況之後編輯程式碼，但未選取 [**未處理的例外狀況回溯呼叫堆疊**] 選項。  
  
- 您嘗試在進行內嵌執行階段應用程式偵錯時編輯程式碼。  
  
- 您嘗試在您附加的程式中編輯程式碼，而不是從 [ **調試** 程式] 功能表開始。  
  
- 您嘗試編輯最佳化程式碼。  
  
- 您嘗試在目標為 64 位元應用程式時編輯 Managed 程式碼。 如果要使用 [編輯後繼續]，就必須將目標設定為 x86  [ (*專案***屬性**]、[**編譯**] 索引標籤、[ **Advanced 編譯器**] 設定。 ) 。  
  
- 您嘗試在已於偵錯期間修改且已重新載入的組譯碼中編輯程式碼。  
  
- 您嘗試編輯尚未載入之組譯碼中的程式碼。  
  
- 您已開始偵錯舊版的應用程式 (因為新版本有建置錯誤)。  
  
- 您嘗試在程式碼正在執行時編輯該程式碼。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **確定**  
 結束對話方塊，並取消緊接在前的編輯嘗試。  
  
## <a name="see-also"></a>另請參閱  
 [ (c + +) 支援的程式碼變更 ](../debugger/supported-code-changes-cpp.md)
