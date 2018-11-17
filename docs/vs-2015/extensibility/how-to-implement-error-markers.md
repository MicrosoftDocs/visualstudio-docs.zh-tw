---
title: 如何： 實作錯誤標記 |Microsoft Docs
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
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e4dd15f4cbb36ef1f81d3b7ca345a6a06bdaff4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736191"
---
# <a name="how-to-implement-error-markers"></a>如何： 實作錯誤標記
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

錯誤標記 （或紅色的波浪底線） 是最困難的文字編輯器自訂項目，來實作。 不過，它們提供給使用者的 VSPackage 的好處遠超過為他們提供的成本。 錯誤標記稍微標記您的語言剖析器認為正確曲線或波浪式紅色底線的文字。 此指標會以視覺化方式顯示不正確的程式碼，以協助程式設計人員。  
  
 您可以使用文字標記來實作紅色的波浪底線。 因此，語言服務加入紅色波浪底線文字緩衝區作為背景通過 」，在閒置時間，或在背景執行緒中。  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>若要實作紅色波浪底線功能  
  
1. 選取想要放置的紅色波浪底線的文字。  
  
2. 建立型別的標記`MARKER_CODESENSE_ERROR`。 如需詳細資訊，請參閱 <<c0> [ 如何： 新增標準的文字標記](../extensibility/how-to-add-standard-text-markers.md)。  
  
3. 在那之後，傳入<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面指標。  
  
   此程序也可讓您透過指定的標記建立提示文字或特殊的內容功能表。 如需詳細資訊，請參閱 <<c0> [ 如何： 新增標準的文字標記](../extensibility/how-to-add-standard-text-markers.md)。  
  
   需要下列物件時，才能夠顯示錯誤標記。  
  
- 剖析器。  
  
- 工作提供者 (也就是實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>)，以找出重新剖析程式會保留行資訊中的變更記錄。  
  
- 文字檢視篩選條件，用來擷取插入號變更事件 檢視使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) 方法。  
  
  剖析器、 工作提供者，以及篩選器提供，讓錯誤標記必要的基礎結構。 下列步驟提供此程序顯示錯誤標記。  
  
1.  在正在進行篩選檢視中，篩選會取得與該檢視的資料相關聯的工作提供者的指標。  
  
    > [!NOTE]
    >  您可以使用相同的命令篩選方法秘訣、 陳述式完成、 錯誤標記和等等。  
  
2.  當篩選條件收到的事件可表示您已經移動到另一行時，工作會檢查有錯誤。  
  
3.  工作處理常式會檢查是否已變更的行。 如果是的話，它會剖析錯誤的行。  
  
4.  如果發現錯誤，工作提供者會建立工作項目執行個體。 這個執行個體建立環境做為錯誤標記文字檢視中的文字標記。  
  
## <a name="see-also"></a>另請參閱  
 [使用舊版 API 中的文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何： 新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)   
 [如何： 建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)   
 [如何：使用文字標記](../extensibility/how-to-use-text-markers.md)

