---
title: 受控偵錯：建議的屬性設定 |Microsoft Docs
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
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f63e1382d242a679ed4fac09bfb3040200fed551
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945295"
---
# <a name="managed-debugging-recommended-property-settings"></a>受控偵錯：建議的屬性設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在所有 Managed 偵錯案例中，某些屬性必須以相同的方式設定。  
  
 下表顯示建議的屬性設定。  
  
 此處未列出的設定，可能會因不同的 Managed 專案類型而異。 例如，Windows Forms 專案中的 [起始動作] 設定，會與 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 專案中的設定不同。  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>建置 (C#) 或編譯 (Visual Basic) 索引標籤上的組態屬性  
  
|**屬性名稱**|**設定**|  
|-----------------------|-----------------|  
|**定義 DEBUG 常數**|C#和F#:設定核取此核取方塊。 這可以讓應用程式使用 Debug 類別。|  
|**定義 TRACE 常數**|C#和F#:設定核取此核取方塊。 這可以讓應用程式使用 Trace 類別。|  
|**最佳化程式碼**|C#F#，和 Visual Basic:設定為 false。 最佳化程式碼較難偵錯，因為產生的指令不能直接對應到您的原始程式碼。 如果您發現程式有一個只出現在最佳化程式碼中的 Bug，您可以開啟這個設定，但是請記住，顯示在 [反組譯碼] 視窗中的程式碼是由最佳化程式碼所產生，可能無法對應至您在程式碼編輯器中看到的內容。 若要偵錯最佳化程式碼，您必須關閉[Just My Code](just-my-code.md)。<br /><br /> 如需詳細資訊，請參閱 < [C# 偵錯組態的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)或是[Visual Basic 偵錯組態的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)。|  
|**輸出路徑**|設定為 bin\Debug\\。|  
|**進階編譯選項**|僅限 Visual Basic。 按一下 [進階] 按鈕以設定下表中描述的進階屬性。|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>進階編譯器設定對話方塊  
  
|**屬性名稱**|**設定**|  
|-----------------------|-----------------|  
|**啟用最佳化**|設定為 false，在指定的原因**最佳化程式碼**上表中的選項。|  
|**產生偵錯資訊**|選取這個核取方塊讓 /DEBUG 旗標在編譯期間被設定，如此一來就會產生協助偵錯所需的資訊。|  
|**定義 DEBUG 常數**|選取這個核取方塊定義 `DEBUG` 常數，讓應用程式能使用 <xref:System.Diagnostics.Debug> 類別。|  
|**定義 TRACE 常數**|選取這個核取方塊定義 `TRACE` 常數，讓應用程式能使用 <xref:System.Diagnostics.Trace> 類別。|  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [C#、F# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
