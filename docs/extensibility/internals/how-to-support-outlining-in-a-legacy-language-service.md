---
title: HOW TO：支援舊版語言服務中的大綱 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3e51b973a358f34c14592a241129ac5fdc7c80d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992967"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>HOW TO：支援舊版語言服務中的大綱
大綱來展開或摺疊文字的不同區域。 方式大綱用定義不同的語言不同。 如需詳細資訊，請參閱[大綱](../../ide/outlining.md)。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解實作大綱的新方式，請參閱[逐步解說：大綱](../../extensibility/walkthrough-outlining.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。  
  
 以下示範如何為您的語言服務支援此命令。  
  
## <a name="to-support-outlining"></a>若要支援大綱  
  
1.  實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage>上您的語言服務物件。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>針對目前的大綱工作階段物件來新增新的外框區域。  
  
## <a name="robust-programming"></a>穩固程式設計  
 當使用者選取**摺疊至定義**上**大綱**功能表，IDE 會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A>您語言的服務。  
  
 IDE 呼叫這個方法時，會傳入<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>指標 （文字緩衝區的指標） 和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>（目前的大綱工作階段的指標）。  
  
 您可以呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>方法來指定這些區域中的多個大綱區域`rgOutlnReg`參數。 `rgOutlnReg`參數是<xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion>結構。 此程序可讓您指定不同的特性，隱藏的區域，例如特定的區域是否為展開或摺疊。  
  
> [!NOTE]
>  小心隱藏新行字元。 隱藏的文字應該擴充從第一行的開始到最後一個字元的最後一行在區段中，保留的最後一個新行字元顯示。  
  
## <a name="see-also"></a>另請參閱  
 [如何：可在舊版語言服務中的隱藏的文字](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [如何：提供展開大綱的支援，在舊版語言服務](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)