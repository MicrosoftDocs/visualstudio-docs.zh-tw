---
title: "如何： 支援舊版語言服務中的大綱 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa57b0d09cb8422a9dde1f70306d2f3808b0384e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>如何： 支援舊版語言服務中的大綱
大綱用來展開或摺疊的文字不同的區域。 使用方式大綱定義不同的語言不同。 如需詳細資訊，請參閱[大綱](../../ide/outlining.md)。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要了解有關實作大綱的新方法的詳細資訊，請參閱[逐步解說： 大綱](../../extensibility/walkthrough-outlining.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
 下列示範如何為您的語言服務支援這個命令。  
  
### <a name="to-support-outlining"></a>若要支援大綱  
  
1.  實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage>語言服務物件上。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>来加入新的大綱區域的目前大綱工作階段物件上。  
  
## <a name="robust-programming"></a>穩固程式設計  
 當使用者選取**摺疊至定義**上**大綱**功能表，IDE 會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A>語言服務上。  
  
 IDE 呼叫這個方法時，會傳入<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>指標 （文字緩衝區的指標） 和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>（目前大綱的工作階段的指標）。  
  
 您可以呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>方法藉由指定這些區域中的多個大綱區域`rgOutlnReg`參數。 `rgOutlnReg`參數是<xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion>結構。 這個程序可讓您指定不同的隱藏區域，例如特定區域是展開還是摺疊的特性。  
  
> [!NOTE]
>  請小心隱藏新行字元。 隱藏的文字應該擴充第一行的開始到最後一個字元的最後一個區段中的一行，並只顯示最後一個新行字元。  
  
## <a name="see-also"></a>請參閱  
 [如何： 隱藏的文字中提供支援舊版語言服務](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [如何︰在舊版語言服務中提供展開大綱的支援](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)