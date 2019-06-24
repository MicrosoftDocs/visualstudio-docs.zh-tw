---
title: 包含語言 |Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d48232ffe6bdc4535f52ed3e2a66a18147352112
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341751"
---
# <a name="contained-languages"></a>包含的語言

*包含語言*都是包含其他語言的語言。 例如，在 HTML[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]頁面可能會包含[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]或[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]指令碼。 雙重語言架構是為了 *.aspx*檔案編輯器中提供 IntelliSense、 顏色標示、 和其他編輯功能的 HTML 和指令碼語言。

## <a name="implementation"></a>實作

您需要實作包含語言的最重要介面是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>介面。 此介面被實作任何裝載於主要語言的語言。 它可讓存取語言服務的色彩標示器、 文字檢視篩選條件和主要語言服務識別碼。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>可讓您建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>介面。 下列步驟會示範如何實作所包含的語言：

1. 使用`QueryService()`為其取得語言服務識別碼和的介面 ID <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>。

2. 若要建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>介面，請呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A>方法。 傳遞<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>介面，一個或多個[項目識別碼](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)，和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>介面。

3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>介面，也就是文字緩衝區協調器物件，提供對應到第二個語言的緩衝區中主要檔案的位置所需的基本服務。

     例如，在單一 *.aspx*檔案中，主要的檔案包括 ASP、 HTML 和包含的所有程式碼。 不過，次要的緩衝區會包含只包含程式碼以及任何類別定義，讓次要緩衝區，有效的程式碼檔案。 緩衝區協調器會處理協調從一個緩衝區之間的編輯的工作。

4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>方法，也就是主要的語言，會告訴緩衝區協調器什麼其緩衝區內的文字會對應到相對應的文字，第二個緩衝區中。

     會將陣列中的語言<xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping>結構，以及目前只包含主要和次要的範圍。

5. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>方法和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A>方法提供的對應，從主要到次要緩衝區，反之亦然。