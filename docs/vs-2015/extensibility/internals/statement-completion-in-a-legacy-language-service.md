---
title: 舊版語言服務中的陳述式完成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d88ebe84ec3ec5efb1d7c4ac04ebaee50ac65b97
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796489"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>舊版語言服務中的陳述式完成
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

完成陳述式是由其語言服務可協助使用者完成語言關鍵字或其已開始在核心編輯器中輸入的項目程序。 本主題討論陳述式完成的運作方式，以及如何在您的語言服務中實作。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解實作陳述式完成的新方式，請參閱[逐步解說： 顯示陳述式完成](../../extensibility/walkthrough-displaying-statement-completion.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="implementing-statement-completion"></a>實作的陳述式完成  
 在核心編輯器中，陳述式完成就會啟動一種特殊的 UI，以互動方式可幫助您更輕鬆地和快速撰寫程式碼。 陳述式完成可協助藉由顯示相關的物件或類別時所需之以避免您不必記住的特定項目，也需要查閱說明參考主題中。  
  
 若要實作陳述式完成，您的語言都必須有陳述式完成觸發程序，可加以剖析。 例如，[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]會使用點 （.） 運算子，而[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]使用箭號 (->) 運算子。 語言服務可以使用一個以上的觸發程序，來起始陳述式完成。 這些觸發程序被撰寫命令篩選器。  
  
## <a name="command-filters-and-triggers"></a>命令篩選器和觸發程序  
 命令篩選器會攔截您的觸發程序或觸發程序的次數。 若要將命令篩選器加入至檢視中，實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，並將它附加到檢視中，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法。 您可以使用相同的命令篩選器 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) 您的語言服務，例如陳述式完成、 錯誤標記和方法秘訣的各個層面。 如需詳細資訊，請參閱 <<c0> [ 攔截舊版語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)。  
  
 在編輯器中輸入該觸發程序時，具體而言，文字緩衝區，語言服務接著會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法。 這會導致以顯示 UI，讓使用者可以選擇從陳述式完成的候選項目編輯器。 這個方法會要求您實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>而<xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags>做為參數的旗標。 捲動清單方塊中顯示的完成項目清單。 在使用者繼續輸入，在清單方塊選取項目會更新以反映最符合的最新的字元類型。 核心編輯器實作陳述式完成的 UI，但語言服務必須實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>介面來定義一組候選項目陳述式的完成項目。  
  
## <a name="see-also"></a>另請參閱  
 [攔截舊版語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

