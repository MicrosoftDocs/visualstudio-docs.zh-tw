---
title: 如何：執行錯誤標記 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2af9e0765fb5bc73a35bebfc2f50f5d2a41122d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838948"
---
# <a name="how-to-implement-error-markers"></a>如何：實作錯誤標記
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

錯誤標記 (或紅色波浪底線) 是要執行的文字編輯器自訂最困難的專案。 不過，他們提供給 VSPackage 使用者的優點，可能遠超過提供它們的成本。 錯誤標記：您的語言剖析器以彎曲或波浪式紅線認為不正確的標記文字。 此指標可協助程式設計人員以視覺化方式顯示不正確的程式碼。  
  
 使用文字標記來執行紅色波浪底線。 作為規則，語言服務會在閒置時間或背景執行緒中，將文字緩衝區的紅色波浪底線新增為背景傳遞。  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>若要執行紅色波浪線功能  
  
1. 選取您要放置紅色波浪底線的文字。  
  
2. 建立類型的標記 `MARKER_CODESENSE_ERROR` 。 如需詳細資訊，請參閱 [如何：新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)。  
  
3. 之後，傳入 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 介面指標。  
  
   此程式也可讓您在指定的標記上建立秘訣文字或特殊的內容功能表。 如需詳細資訊，請參閱 [如何：新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)。  
  
   您必須要有下列物件，才能顯示錯誤標記。  
  
- 剖析器。  
  
- 工作提供者 (也就是，會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> 維護行資訊中變更記錄的) 的執行，以便識別要重新剖析的行。  
  
- 使用) 方法，從視圖中捕捉插入點變更事件的文字視圖篩選 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A> 。  
  
  剖析器、工作提供者和篩選器提供必要的基礎結構，讓您可以進行錯誤標記。 下列步驟提供顯示錯誤標記的程式。  
  
1. 在要篩選的視圖中，篩選會取得與該視圖資料相關聯之工作提供者的指標。  
  
    > [!NOTE]
    > 您可以使用相同的命令篩選器來取得方法提示、語句完成、錯誤標記等等。  
  
2. 當篩選準則收到事件指出您已移至另一行時，就會建立一個工作來檢查錯誤。  
  
3. 工作處理常式會檢查該行是否已變更。 如果是，則會剖析錯誤的行。  
  
4. 如果發現錯誤，工作提供者會建立工作專案實例。 此實例會在文字視圖中建立環境用來做為錯誤標記的文字標記。  
  
## <a name="see-also"></a>另請參閱  
 [搭配舊版 API 使用文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何：新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)   
 [如何：建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)   
 [如何：使用文字標記](../extensibility/how-to-use-text-markers.md)
