---
title: 包含語言 |Microsoft 文件
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbf2c63a66ba76b65d1caec2c5eed006d57fca0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109762"
---
# <a name="contained-languages"></a>所包含的語言

*包含語言*會包含在其他語言的語言。 例如，在 HTML[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]頁面可能會包含[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]或[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]指令碼。 雙重語言架構是為了.aspx 檔案編輯器，HTML 和指令碼語言提供 IntelliSense、 顏色標示、 和其他的編輯功能。

## <a name="implementation"></a>實作

最重要的介面，您需要實作所包含的語言是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>介面。 這個介面是由任何可以裝載於主要語言的語言實作。 它可讓存取語言服務的色彩標示器、 文字檢視篩選條件，以及主要語言服務識別碼。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>可讓您建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>介面。 下列步驟顯示如何實作所包含的語言：

1.  使用`QueryService()`取得語言服務識別碼和的介面 ID <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>。

2.  若要建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>介面，請呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A>方法。 傳遞<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>介面，一個或多個[項目識別碼](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)，和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>介面。

3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>介面，也就是文字緩衝區協調器物件，提供對應到次要語言的緩衝區的位置中主要檔案所需的基本服務。

     例如，在單一的.aspx 檔案中，主要檔案包含 ASP、 HTML 和包含的所有程式碼。 不過，次要緩衝區包含只包含的程式碼以及任何類別定義，以讓次要緩衝區有效的程式碼檔案。 緩衝區協調器會處理協調的編輯內容從一個緩衝區的其他工作。

4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>方法，為主要語言時，會告訴緩衝區協調器什麼其緩衝區內的文字會對應至相對應的文字，第二個緩衝區中。

     傳遞陣列中的語言<xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping>結構，以及目前只包含主要和次要的範圍。

5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>方法和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A>方法以提供從主要及次要緩衝區的對應。