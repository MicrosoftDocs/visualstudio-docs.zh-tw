---
title: "Visual Studio 檔案中尋找和檔案中取代 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8b13903fc02a716de951847ce9409e750764b123
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="replace-in-files"></a>檔案中取代
[檔案中取代] 可讓您在一組指定檔案中搜尋程式碼的字串或運算式，並變更部分或所有找到的相符項目。 在 [結果選項] 內選取的 [尋找結果] 視窗中，會列出找到的相符項目與所採取的動作。  
  
> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更您的設定 (例如變更為 [一般] 或 [Visual C++] 設定)，請選擇 [工具]、[匯入和匯出設定]，然後選擇 [重設所有設定]。
  
您可以使用下列方法之一，在 [檔案中尋找] 視窗中顯示 [檔案中取代]。  
  
### <a name="to-display-replace-in-files"></a>若要顯示檔案中取代  
  
1.  在 [編輯] 功能表上，展開 [尋找和取代]。  
  
2.  選擇 [檔案中取代]。  
  
     — 或 —  
  
     如果 [尋找和取代] 視窗已開啟，請選擇工具列中的 [檔案中取代]。  
  
## <a name="find-what"></a>尋找目標  
若要搜尋新的文字字串或運算式，請在方塊中指定。 若要搜尋您最近搜尋過的 20 筆字串之一，請開啟該清單，並選擇您要搜尋的字串。 如果您想要在搜尋字串中使用一或多個規則運算式，請選擇相鄰的 [運算式產生器] 按鈕。 如需詳細資訊，請參閱[在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。
  
## <a name="replace-with"></a>取代為  
若要將 [尋找目標] 方塊中的字串執行個體取代為其他字串，請在 [取代為] 方塊中輸入取代字串。 若要刪除 [尋找目標] 方塊中的字串執行個體，請將此欄位保留空白。 開啟清單即可顯示您最近搜尋的 20 筆字串。 如果您想要在取代字串中使用一或多個規則運算式，請選擇相鄰的 [運算式產生器] 按鈕。 如需詳細資訊，請參閱[在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。
  
## <a name="look-in"></a>查詢  
[查詢] 下拉式清單中所選擇的選項，可決定 [檔案中取代] 只會搜尋目前作用中的檔案，還是會搜尋所有儲存在特定資料夾內的檔案。 從清單中選取搜尋範圍、輸入資料夾路徑，或按一下 [瀏覽 (...)] 按鈕，顯示 [選擇搜尋資料夾] 對話方塊，然後選擇要搜尋的資料夾集合。 您也可以直接在 [查詢] 方塊中輸入路徑。
  
> [!NOTE]
>  如果選取 [查詢] 選項時，所搜尋的檔案已從原始程式碼控制簽出，則只會搜尋該檔案的本機電腦下載版本。
  
## <a name="find-options"></a>尋找選項  
您可以展開或摺疊 [尋找選項] 區段。 可選取或清除下列選項：  
  
大小寫須相符  
選取時，[尋找結果] 視窗僅會顯示內容和大小寫都相符的 [尋找目標] 字串執行個體。 例如，若搜尋 "MyObject" 時選取 [大小寫須相符]，則會傳回 "MyObject"，而不是 "myobject" 或 "MYOBJECT"。  

全字拼寫須相符  
選取時，[尋找結果] 視窗僅會顯示完整字組相符的 [尋找目標] 字串執行個體。 例如，搜尋 "MyObject" 時會傳回 "MyObject"，而不是 "CMyObject" 或 "MyObjectC"。  

使用規則運算式  
如果已選取此核取方塊，您可以在 [尋找目標] 或 [取代為] 文字方塊中，使用特殊標記法來定義文字模式。 如需這些標記法的清單，請參閱[在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。  

尋找下列檔案類型  
這個清單可指定要在 [查詢] 目錄中搜尋的檔案類型。 如果此欄位保持空白，則會搜尋 [查詢] 目錄中的所有檔案。  

選取此清單中的任一項目，即可輸入預先設定的搜尋字串，以尋找特定類型的檔案。  
  
## <a name="result-options"></a>結果選項  
您可以展開或摺疊 [結果選項] 區段。 可選取或清除下列選項：  

尋找結果 1 視窗  
若選取此選項，目前搜尋的結果將會取代 [尋找結果 1] 視窗的內容。 這個視窗會自動開啟以顯示搜尋結果。 若要手動開啟此視窗，請從 [檢視] 功能表中選取 [其他視窗]，並選擇 [尋找結果 1]。  

尋找結果 2 視窗  
若選取此選項，目前搜尋的結果將會取代 [尋找結果 2] 視窗的內容。 這個視窗會自動開啟以顯示搜尋結果。 若要手動開啟此視窗，請從 [檢視] 功能表中選取 [其他視窗]，並選擇 [尋找結果 2]。  

只顯示檔名  
選取此核取方塊時，[尋找結果] 視窗會列出包含搜尋字串之所有檔案的完整名稱和路徑。 不過，這些結果不含字串出現位置的程式碼行。 此核取方塊僅在 [檔案中尋找] 中提供。  

全部取代後將修改過的檔案保持開啟  
選取時，會將已進行取代作業的所有檔案保持開啟，以便您復原或儲存變更。 由於記憶體有限，因此在取代作業之後可以保持開啟的檔案數目有所限制。  

> [!CAUTION]
>  只有在保持開啟可供編輯的檔案中，才可以使用 [復原]。 如果未選取這個選項，則未開啟以供編輯的檔案將會保持關閉狀態，其中也不會出現 [復原] 選項。  
  
## <a name="see-also"></a>請參閱
[尋找和取代文字](../ide/finding-and-replacing-text.md)   
[檔案中尋找](../ide/find-in-files.md)   
[Visual Studio 命令](../ide/reference/visual-studio-commands.md)