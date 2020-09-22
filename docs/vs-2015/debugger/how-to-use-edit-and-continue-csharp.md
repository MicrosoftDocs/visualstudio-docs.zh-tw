---
title: '如何：使用編輯後繼續 (c # ) |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39137d5fe60a3c91c8fd3904e797eb83420a8f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838997"
---
# <a name="how-to-use-edit-and-continue-c"></a>如何：使用編輯後繼續 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

利用 C# 的 [編輯後繼續]，偵錯時您可以在中斷模式中變更程式碼。 不需要停止並重新啟動偵錯工作階段，就可以套用這些變更。  
  
 當您在中斷模式中進行變更時，會自動叫用 [編輯後繼續]，然後選擇偵錯工具執行命令（例如 [ **繼續**]、[ **逐步**執行 **] 或 [設定下一個語句**]），或在偵錯工具視窗中評估函數。  
  
> [!NOTE]
> 當您將 Compact Framework、優化程式碼、混合原生/managed 程式碼或 SQL Server common language runtime (CLR) 整合程式碼時，不支援 [編輯後繼續]。 如果您嘗試在其中一個案例中套用程式碼變更，偵錯工具會出現一個對話方塊，說明不支援 [編輯後繼續]。  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>若要自動叫用 [編輯後繼續]  
  
1. 在中斷模式中，對您的原始程式碼進行變更。  
  
2. 在 [ **調試** 程式] 功能表中，按一下 [ **繼續**]、[ **逐步執行** **] 或 [設定下一個語句** ]，或在偵錯工具視窗中評估函數  
  
     新的程式碼會進行編譯，而偵錯工具會繼續使用新的程式碼。 [編輯後繼續] 不支援某些變更。 如需詳細資訊，請參閱 [ (c # ) 支援的程式碼變更 ](../debugger/supported-code-changes-csharp.md)。  
  
### <a name="to-enabledisable-edit-and-continue"></a>若要啟用/停用編輯後繼續   
  
1. 在 **[工具]** 功能表上，按一下 **[選項]** 。  
  
2. 在 [ **選項** ] 對話方塊中，展開 [ **調試** ] 節點，然後選取 [ **編輯後繼續**]。  
  
3. 在 [ **選項** ] 對話方塊的 [ **編輯後繼續** ] 頁面中，選取或清除 [ **啟用編輯後繼續** ] 核取方塊。  
  
     當您重新開機調試過程時，此設定就會生效。  
  
## <a name="see-also"></a>另請參閱  
 [Visual c # ) 的 [編輯後繼續] (](../debugger/edit-and-continue-visual-csharp.md)   
 [ (c # ) 支援的程式碼變更 ](../debugger/supported-code-changes-csharp.md)   
 [編輯後繼續的錯誤和警告 (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)
