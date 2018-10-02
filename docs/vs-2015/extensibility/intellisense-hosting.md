---
title: IntelliSense 裝載 |Microsoft Docs
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
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20e2c0d2c14a0191811453b8e1a5cadf3d314e98
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488862"
---
# <a name="intellisense-hosting"></a>IntelliSense 裝載
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[IntelliSense 裝載](https://docs.microsoft.com/visualstudio/extensibility/intellisense-hosting)。  
  
Visual Studio 可讓 IntelliSense 裝載。 IntellSense 裝載可讓您會提供 IntelliSense for Visual Studio 文字編輯器所未裝載的程式碼。  
  
## <a name="intellisense-hosting-usage"></a>IntelliSense 裝載的使用方式  
 在 Visual Studio 中，任何可存取完成設定和文字緩衝區的程式碼可以從任何地方取得 IntelliSense windows 使用者介面 (UI) 中。 這個範例案例會在完成**監看式**視窗或在 [中斷點屬性] 視窗的 [條件] 欄位中。  
  
### <a name="implementation-interfaces"></a>實作介面  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 任何裝載 IntelliSense 快顯視窗的 UI 元件必須支援<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面。 預設核心編輯器文字檢視包含股票<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面實作，以保留目前的 IntelliSense 功能。 大部分的情況下，方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面實作的功能子集，則的代表<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面。 子集包含 IntelliSense UI 處理、 插入號並選取操作和簡單的文字取代功能。 颾魤 ㄛ<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面讓不同的 IntelliSense [主旨] 和 [內容]，讓 IntelliSense 可供直接沒有文字緩衝區所使用的內容中的主題。  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面提供者必須實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A>方法，讓用戶端，來判斷何種類型的 IntelliSense 功能的主機支援。  
  
 中所定義的主應用程式旗標[IntelliSenseHostFlags](../extensibility/intellisensehostflags.md)，以下摘要說明。  
  
|IntelliSense 主機旗標|描述|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|設定此旗標表示內容緩衝區是唯讀模式和編輯內會出現只有主旨文字。|  
|IHF_NOSEPERATESUBJECT|設定此旗標表示有是沒有個別的 IntelliSense 主旨。 主體存在於內容緩衝區，例如在傳統<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>IntelliSense 系統。|  
|IHF_SINGLELINESUBJECT|設定主旨不是此旗標表示多行功能，例如單一行中編輯**監看式**視窗。|  
|IHF_FORCECOMMITTOCONTEXT|設定此旗標，且必須更新的內容緩衝區，如果要忽略的內容緩衝區上的唯讀旗標並繼續編輯，可讓主應用程式。|  
|IHF_OVERTYPE|編輯 （在主旨或內容） 應該在取代模式中。|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit 和 IVsIntellisenseHost.AfterCompletorCommit  
 完成視窗之前和之後的文字經過認可時，若要啟用前置處理和後置處理，會呼叫這些回呼方法。  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor>介面是標準完成視窗中，以供整合式的開發環境 (IDE) 的共同建立版本。 任何<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面可以快速實作 IntelliSense 使用此 completor 介面。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop>

