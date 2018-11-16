---
title: 編輯後繼續 (Visual Basic) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 43
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 383e3418135857b0bded3bbefaace0e8d5832ce6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750635"
---
# <a name="edit-and-continue-visual-basic"></a>編輯後繼續 (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

「編輯後繼續」是 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 偵錯的一個功能，當程式碼在中斷模式中執行時，這項功能可讓您變更程式碼。 套用程式碼編輯之後，您可以繼續以新的編輯執行程式碼，並查看其效果。  
  
 只要進入中斷模式，隨時都可以使用編輯後繼續功能。 在中斷模式中，指令指標 (來源視窗中的黃色箭頭) 會指向接下來要執行的那一行，並且指標將位於方法或屬性主體內的可執行陳述式上。 在中斷模式中，您可以對可執行陳述式進行各種變更，該變更將被加入基礎專案中。 但是在中斷模式中，通常不允許您變更宣告陳述式，例如公用方法、公用欄位或類別宣告。  
  
 當您進行未經授權的編輯時，會以紫色波浪底線標示這個變更，而且 [工作清單] 中會顯示工作。 如果您要繼續使用 [編輯後繼續]，必須復原未經授權的編輯。 如果在 [編輯後繼續] 以外進行某些未經授權的編輯，則可能會允許進行這些編輯。 如果您要保留這種未經授權的編輯結果，必須先停止偵錯並重新啟動應用程式。  
  
 以 .NET Framework 4.5.1 為目標的 64 位元專案支援 [編輯後繼續]。  
  
 編輯後繼續時，不支援您開始使用偵錯**附加至處理序**。 在最佳化程式碼、混合 Managed 程式碼和機器碼或 Compact Framework (智慧型裝置) 專案中，皆不支援 [編輯後繼續] 功能。  
  
 本章節中的主題提供其他詳細資訊，說明使用這項功能的方法以及不允許進行的變更種類。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：以編輯後繼續在中斷模式套用編輯](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 說明在中斷模式中套用程式碼編輯的方式。  
  
 [Visual Basic 編輯後繼續中不支援的編輯](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 描述哪些類型的編輯內容無法在 [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] [編輯後繼續] 中執行。  
  
## <a name="related-sections"></a>相關章節  
 [編輯後繼續](../debugger/edit-and-continue.md)  
 提供編輯後繼續的主題清單。



