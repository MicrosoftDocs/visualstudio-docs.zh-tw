---
title: 如何：在舊版語言服務中支援大綱 |Microsoft Docs
description: 瞭解如何在舊版語言服務中提供大綱、擴充或折迭不同文字區域的支援。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 028d1a9aae21aae8c6368e4eea3820aabd200be6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901795"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>如何：在舊版語言服務中支援大綱
大綱是用來展開或折迭不同的文字區域。 使用大綱的方式可以不同的語言來定義。 如需詳細資訊，請參閱[大綱](../../ide/outlining.md)。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解如何執行大綱的新方法，請參閱 [逐步解說：大綱](../../extensibility/walkthrough-outlining.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

 以下示範如何針對您的語言服務支援此命令。

## <a name="to-support-outlining"></a>支援大綱

1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage>在您的語言服務物件上執行。

2. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 目前大綱的會話物件，以加入新的外框區域。

## <a name="robust-programming"></a>穩固程式設計
 當使用者選取 **大綱** 功能表上的 [折迭 **至定義**] 時，IDE 會 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> 在您的語言服務上呼叫。

 當呼叫這個方法時，IDE 會將指標傳入 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> (文字緩衝區的指標) 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (目前大綱會話) 的指標。

 您可以藉 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 由在參數中指定這些區域，來呼叫多個外框區域的方法 `rgOutlnReg` 。 `rgOutlnReg`參數是一個 <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> 結構。 此程式可讓您指定隱藏區域的不同特性，例如特定區域是否展開或折迭。

> [!NOTE]
> 請小心隱藏換行字元。 隱藏文字應從第一行的開頭擴充到區段最後一行的最後一個字元，使最後的新行字元保持可見。

## <a name="see-also"></a>另請參閱
- [如何：在舊版語言服務中提供隱藏文字支援](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [如何：在舊版語言服務中提供展開大綱支援](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
