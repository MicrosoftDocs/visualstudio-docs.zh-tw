---
title: 包含的語言 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0920999eee7460c8bf697e245bae55a3641b8e18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184288"
---
# <a name="contained-languages"></a>包含的語言
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

*包含的語言* 是其他語言所包含的語言。 例如，頁面中的 HTML [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 可能包含 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 或 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 腳本。 .Aspx 檔編輯器需要雙重語言架構，以提供 HTML 和指令碼語言的 IntelliSense、顏色標示和其他編輯功能。  
  
## <a name="implementation"></a>實作  
 您必須為包含的語言執行最重要的介面，就是 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 介面。 此介面是由可裝載于主要語言內的任何語言所執行。 它會提供語言服務的著色器、文字視圖篩選和主要語言服務識別碼的存取權。 可 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> 讓您建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 介面。 下列步驟說明如何執行包含的語言：  
  
1. 使用 `QueryService()` 取得的語言服務識別碼和介面識別碼 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> 。  
  
2. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> 方法來建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 介面。 傳遞 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 介面、一或多個 [專案識別碼](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> 介面。  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>介面（文字緩衝區協調器物件）提供將主要檔案中的位置對應到次要語言緩衝區所需的基本服務。  
  
     例如，在單一 .aspx 檔案中，主要檔案包含 ASP、HTML 以及包含的所有程式碼。 不過，次要緩衝區只包含包含的程式碼以及任何類別定義，讓次要緩衝區成為有效的程式碼檔案。 緩衝區協調器會處理將編輯從某個緩衝區協調到另一個緩衝區的工作。  
  
4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>方法（主要語言）會告知緩衝區協調器，其緩衝區內的哪些文字會對應到次要緩衝區中的對應文字。  
  
     語言會傳入結構的陣列，此陣列 <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> 目前只包含主要和次要範圍。  
  
5. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>方法和方法會 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> 提供從主要緩衝區到次要緩衝區的對應，反之亦然。
