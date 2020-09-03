---
title: IntelliSense 裝載 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c378aec6822a436de0d8fc2656fcac7be4149f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203904"
---
# <a name="intellisense-hosting"></a>IntelliSense 裝載
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 可啟用 IntelliSense 裝載。 IntellSense 裝載可讓您為非由 Visual Studio 文字編輯器所裝載的程式碼提供 IntelliSense。  
  
## <a name="intellisense-hosting-usage"></a>IntelliSense 裝載使用方式  
 在 Visual Studio 中，任何可存取完成集和文字緩衝區的程式碼都可以從使用者介面的任何位置取得 IntelliSense 視窗 (UI) 。 某些範例案例會在 [ **監看** 式] 視窗或 [中斷點屬性] 視窗的 [條件] 欄位中完成。  
  
### <a name="implementation-interfaces"></a>實介面  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 裝載 IntelliSense 快顯視窗的任何 UI 元件都必須支援 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 介面。 預設的 [核心編輯器] 文字視圖包含 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 可保留目前 IntelliSense 功能的內建介面。 在大部分的情況下，介面的方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 代表在介面上實作為的子集 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 。 子集包括 IntelliSense UI 處理、插入號和選取範圍的操作，以及簡單的文字取代功能。 此外，介面還 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 可啟用不同的 intellisense 「主旨」和「內容」，以便為不會直接存在於內容的文字緩衝區中的主體提供 intellisense。  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面提供者必須執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> 方法，才能讓用戶端判斷主機支援何種 IntelliSense 功能。  
  
 [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md)中定義的主機旗標摘要如下。  
  
|IntelliSense 主機旗標|描述|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|設定此旗標表示內容緩衝區是唯讀的，而且只會在主體文字內進行編輯。|  
|IHF_NOSEPERATESUBJECT|設定此旗標表示沒有個別的 IntelliSense 主體。 主體存在於內容緩衝區中，例如傳統的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> IntelliSense 系統。|  
|IHF_SINGLELINESUBJECT|設定此旗標表示主體並非多行功能，例如在 [ **監看** 式] 視窗中的單一行編輯。|  
|IHF_FORCECOMMITTOCONTEXT|如果設定此旗標，而且必須更新內容緩衝區，主機會在內容緩衝區上啟用唯讀旗標以進行忽略，並繼續進行編輯。|  
|IHF_OVERTYPE|在 [主體] 或 [內容]) 中編輯 (應該在 [改寫] 模式中完成。|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost. BeforeCompletorCommit 和 IVsIntellisenseHost. AfterCompletorCommit  
 在認可文字之前和之後，完成視窗會呼叫這些回呼方法，以啟用前置處理和後置處理。  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor>介面是標準完成視窗的可共同建立版本，可供整合式開發環境 (IDE) 使用。 任何 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 介面都可以使用這個 completor 介面快速執行 IntelliSense。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
