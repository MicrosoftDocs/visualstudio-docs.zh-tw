---
title: "如何： 隱藏的文字中提供支援舊版語言服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7aab5978d2fc5f7bee82b097ed61a9603d7e198
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>如何： 隱藏的文字中提供支援舊版語言服務
您可以建立大綱區域除了隱藏的文字區域。 用戶端控制或編輯器控制，可以是隱藏的文字區域，可用於完全隱藏的文字區域。 編輯器會顯示為水平線隱藏的區域。 舉例來說，這是在 HTML 編輯器中的 [僅限指令碼] 檢視。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-implement-a-hidden-text-region"></a>若要實作隱藏的文字區域  
  
1.  呼叫`QueryService`如<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>。  
  
     這將指標傳回至<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>傳遞給指定的文字緩衝區的指標。 這會決定是否隱藏的文字工作階段已經存在的緩衝區。  
  
3.  如果已經存在，則您不需要建立一個，現有的指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>物件傳回。 列舉及建立隱藏的文字區域中使用這個指標。 否則，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>建立隱藏的文字的工作階段緩衝區。  
  
     指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>物件傳回。  
  
    > [!NOTE]
    >  當您呼叫`CreateHiddenTextSession`，您可以指定隱藏的文字用戶端 (也就是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>)。 展開或摺疊，只要使用者隱藏的文字或大綱時，隱藏的文字用戶端會通知您。  
  
4.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>加入一個或多新區域概述一次，指定下列資訊在`reHidReg`(<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) 參數：  
  
    1.  指定的值為`hrtConcealed`中`iType`隸屬<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構，以指出您要建立隱藏的區域，而不是一個大綱區域。  
  
        > [!NOTE]
        >  隱藏的區域隱藏時，編輯器會自動顯示隱藏的區域，以指出其周圍的行。  
  
    2.  指定區域是用戶端控制，或在控制編輯器`dwBehavior`成員<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構。 智慧大綱實作可以包含混合的控制編輯器和用戶端的外框和隱藏的文字區域。