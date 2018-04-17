---
title: 如何： 實作錯誤標記 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d41c1bf063ea074df217934a00f73291a10e051d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-error-markers"></a>如何： 實作錯誤標記
錯誤標記 （或紅色波浪底線） 是最困難的文字編輯器的自訂實作。 不過，它們提供給使用者的 VSPackage 的好處遠超過為他們提供的成本。 錯誤標記稍微標示您的語言剖析器認為正確曲線或波浪式紅色底線的文字。 此指標會協助程式設計人員，以視覺化方式顯示不正確的程式碼。  
  
 您可以使用文字標記來實作紅色波浪底線顯示。 規則，語言服務加入紅色波浪底線文字緩衝的背景傳遞，以在閒置時或在背景執行緒中。  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>實作紅色波浪底線功能  
  
1.  選取您想要在其下放置紅色波浪底線的文字。  
  
2.  建立類型的標記`MARKER_CODESENSE_ERROR`。 如需詳細資訊，請參閱[如何： 加入標準文字標記](../extensibility/how-to-add-standard-text-markers.md)。  
  
3.  在這之後，傳入<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面指標。  
  
 此程序也可讓您建立透過指定標記的提示文字或特殊的內容功能表。 如需詳細資訊，請參閱[如何： 加入標準文字標記](../extensibility/how-to-add-standard-text-markers.md)。  
  
 在顯示錯誤標記之前，所需下列物件。  
  
-   剖析器。  
  
-   工作提供者 (也就是實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>)，以找出要重新剖析的行維護記錄的資訊列中的變更。  
  
-   擷取插入號文字檢視篩選條件變更事件 檢視使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) 方法。  
  
 剖析器、 工作提供者，以及篩選提供的基礎結構，讓可能的錯誤標記。 下列步驟提供的程序顯示的錯誤標記。  
  
1.  在進行篩選檢視中，篩選會取得與該檢視資料相關聯之工作提供者的指標。  
  
    > [!NOTE]
    >  您可以使用相同的命令篩選方法秘訣、 陳述式完成、 錯誤標記等等。  
  
2.  當篩選條件收到事件，指出您已移到另一條時，會建立一個工作，檢查有錯誤。  
  
3.  工作處理常式會檢查行是否已變更。 如果是的話，它會剖析錯誤的行。  
  
4.  如果發現錯誤，則工作提供者會建立工作項目執行個體。 這個執行個體建立環境會使用做為文字檢視中的錯誤標記的文字標記。  
  
## <a name="see-also"></a>請參閱  
 [使用文字標記與舊版應用程式開發介面](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何： 加入標準文字標記](../extensibility/how-to-add-standard-text-markers.md)   
 [如何： 建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)   
 [如何： 使用文字標記](../extensibility/how-to-use-text-markers.md)