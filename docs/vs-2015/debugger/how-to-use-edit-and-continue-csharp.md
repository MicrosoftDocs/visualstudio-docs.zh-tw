---
title: 如何： 使用編輯後繼續 (C#) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 536a54958154a8ec4741ea979f70caf7183dbd12
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298333"
---
# <a name="how-to-use-edit-and-continue-c"></a>如何：使用編輯後繼續 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

利用 C# 的 [編輯後繼續]，偵錯時您可以在中斷模式中變更程式碼。 不需要停止並重新啟動偵錯工作階段，就可以套用這些變更。  
  
 編輯後繼續時所叫用會自動在中斷模式中進行變更，然後選擇 偵錯工具執行命令，例如**繼續**，**步驟**，或**設定下一個陳述式**，或評估在偵錯工具視窗中的函式。  
  
> [!NOTE]
>  Compact Framework，也就是最佳化的程式碼進行偵錯混合原生 /managed 程式碼或 SQL Server common language runtime (CLR) 整合程式碼時，不支援編輯後繼續。 如果您嘗試套用程式碼變更任一這些案例中的，偵錯工具會對話方塊方塊中，說明不支援 編輯後繼續。  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>若要叫用 編輯後自動繼續  
  
1.  在中斷模式，請對原始程式碼進行變更。  
  
2.  從**偵錯**功能表上，按一下**繼續**，**步驟**，或**設定下一個陳述式**或評估在偵錯工具視窗中的函式。  
  
     新的程式碼會編譯和偵錯會繼續進行新的程式碼。 編輯後繼續不支援某些變更。 如需詳細資訊，請參閱 <<c0> [ 支援的程式碼變更 (C#)](../debugger/supported-code-changes-csharp.md)。  
  
### <a name="to-enabledisable-edit-and-continue"></a>若要啟用/停用編輯後繼續   
  
1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
2.  在 **選項**對話方塊方塊中，展開**偵錯**節點，然後選取**編輯後繼續**。  
  
3.  在 [**選項**] 對話方塊中**編輯後繼續**頁面上，選取或清除**啟用編輯後繼續**核取方塊。  
  
     當您重新啟動偵錯工作階段時，這個設定會生效。  
  
## <a name="see-also"></a>另請參閱  
 [編輯後繼續 (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [支援的程式碼變更 (C#)](../debugger/supported-code-changes-csharp.md)   
 [編輯後繼續的錯誤和警告 (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)



