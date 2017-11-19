---
title: "IntelliSense 裝載 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 850e4b2ef6d455bb141827fa125c4c7c6860b652
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="intellisense-hosting"></a>IntelliSense 裝載
Visual Studio 可讓 IntelliSense 裝載。 IntellSense 裝載可讓您會提供 IntelliSense 程式碼的 Visual Studio 文字編輯器所未裝載。  
  
## <a name="intellisense-hosting-usage"></a>IntelliSense 裝載使用量  
 在 Visual Studio 中，已完成，以及文字緩衝區的存取的任何程式碼可以從任何地方取得 IntelliSense windows 使用者介面 (UI) 中。 一些範例案例，這會在完成**監看式**視窗或中斷點屬性 視窗的 條件 欄位。  
  
### <a name="implementation-interfaces"></a>實作介面  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 任何裝載 IntelliSense 快顯視窗的 UI 元件必須支援<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面。 預設核心編輯器文字檢視包含內建<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面實作來保留目前的 IntelliSense 功能。 大部分的情況下，方法的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面實作的功能子集代表<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面。 子集包含 IntelliSense UI 處理、 插入號並選取操作和簡單的文字取代功能。 此外，<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面可讓個別的 IntelliSense"subject"和 「 內容 」 讓 IntelliSense 可供不直接存在於用於內容的文字緩衝的主旨。  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面提供者必須實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A>方法，讓用戶端，以判斷哪種類型的 IntelliSense 功能的主機支援。  
  
 中所定義的主應用程式旗標[IntelliSenseHostFlags](../extensibility/intellisensehostflags.md)，以下摘要說明。  
  
|IntelliSense 主機旗標|說明|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|設定此旗標表示的內容緩衝區是唯讀和編輯，就會發生只在主旨文字。|  
|IHF_NOSEPERATESUBJECT|設定這個旗標表示有是沒有個別的 IntelliSense 主旨。 主旨存在於內容緩衝區中，例如在傳統<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>IntelliSense 系統。|  
|IHF_SINGLELINESUBJECT|設定這個旗標表示主體已不多行功能，例如在單一行中編輯**監看式**視窗。|  
|IHF_FORCECOMMITTOCONTEXT|設定此旗標，且必須更新的內容緩衝區，如果要忽略的內容緩衝區上的唯讀旗標，以繼續編輯，可讓主應用程式。|  
|IHF_OVERTYPE|編輯 （在主旨或內容） 應該在取代模式中執行。|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit 和 IVsIntellisenseHost.AfterCompletorCommit  
 之前與之後的文字會被認可，若要啟用預先處理和後置處理，則完成視窗會呼叫這些回呼方法。  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor>介面是共同建立版本的整合式的開發環境 (IDE) 由標準完成視窗。 任何<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面可以使用此 completor 介面來快速實作 IntelliSense。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop>