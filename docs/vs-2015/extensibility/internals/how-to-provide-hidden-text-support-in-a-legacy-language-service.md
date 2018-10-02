---
title: 如何： 隱藏的文字中提供支援舊版語言服務 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b689bdfff45f12bc85f79b3cba8581e728c89728
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488918"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>如何： 隱藏的文字中提供支援舊版語言服務
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 提供隱藏文字中的支援舊版語言服務](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service)。  
  
您可以建立大綱區域除了隱藏的文字區域。 用戶端控制或編輯器控制，可以是隱藏的文字區域，並用來完全隱藏的文字區域。 編輯器會顯示為水平線的隱藏的區域。 這個範例是 HTML 編輯器中的 [僅限指令碼] 檢視。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-implement-a-hidden-text-region"></a>若要實作的隱藏的文字區域  
  
1.  呼叫`QueryService`針對<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>。  
  
     這會傳回的指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>，傳入指定的文字緩衝區的指標。 這會決定是否隱藏的文字的工作階段已存在的緩衝區。  
  
3.  如果已經存在，則您不需要建立一個，現有的指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>會傳回物件。 列舉及建立隱藏的文字區域中使用這個指標。 否則，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>建立隱藏的文字的工作階段緩衝區。  
  
     指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>會傳回物件。  
  
    > [!NOTE]
    >  當您呼叫`CreateHiddenTextSession`，您可以指定隱藏的文字，用戶端 (也就是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>)。 隱藏的文字或大綱展開或摺疊，只要使用者時，隱藏的文字用戶端會通知您。  
  
4.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>新增一或多新區域概述一次，指定下列資訊`reHidReg`(<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) 參數：  
  
    1.  指定的值為`hrtConcealed`中`iType`隸屬<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構，以指出您要建立隱藏的區域，而不是一個大綱區域。  
  
        > [!NOTE]
        >  隱藏的區域隱藏時，編輯器會自動顯示隱藏的區域，以指出其存在周圍的線條。  
  
    2.  指定的區域是用戶端控制，或以控制編輯器`dwBehavior`的成員<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構。 智慧型大綱實作可以包含各種編輯器和用戶端控制的大綱和隱藏的文字區域。

