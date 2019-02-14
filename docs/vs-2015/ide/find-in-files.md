---
title: 檔案中尋找 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 430f2a55f180428c781e7a8cbe1f78d3a0355128
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804355"
---
# <a name="find-in-files"></a>檔案中尋找
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[檔案中尋找] 可讓您搜尋一組指定的檔案。 在 [結果選項] 內選取的 [尋找結果] 視窗中，會列出找到的相符項目與所採取的動作。  
  
 您可以使用下列任何方法，以在 [尋找和取代] 視窗中顯示 [檔案中尋找]。  
  
### <a name="to-display-find-in-files"></a>顯示檔案中尋找  
  
1. 在功能表列上，依序選擇 [編輯] 和 [尋找和取代]。  
  
2. 選擇 [檔案中尋找]。  
  
   若要取消尋找作業，請按 CTRL + BREAK。  
  
> [!NOTE]
>  [尋找和取代] 工具不會搜尋目錄與 `Hidden` 或 `System` 屬性集。  
  
## <a name="find-what"></a>尋找目標  
 若要搜尋新的文字字串或運算式，請在方塊中指定。 若要搜尋您最近搜尋過的 20 筆字串之一，請開啟該清單，並選擇您要搜尋的字串。 如果您想要在搜尋字串中使用一或多個規則運算式，請選擇相鄰的 [運算式產生器] 按鈕。 如需詳細資訊，請參閱[在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。  
  
## <a name="look-in"></a>查詢  
 [查詢] 下拉式清單中所選擇的選項，可決定 [檔案中尋找] 只會搜尋目前使用中檔案，或搜尋所有儲存在特定資料夾內的檔案。 從清單中選取搜尋範圍，或按一下 [瀏覽 (...)] 按鈕，顯示 [選擇搜尋資料夾] 對話方塊，然後輸入您本身的目錄集。 您也可以直接在 [查詢] 方塊中輸入路徑。  
  
> [!WARNING]
>  使用 [整個方案] 或 [目前專案] 選項時，並不會搜尋專案和方案檔。 如果您想查詢專案檔，請選擇搜尋資料夾。  
  
> [!NOTE]
>  如果選取 [查詢] 選項時，所搜尋的檔案已從原始程式碼控制簽出，則只會搜尋該檔案的本機電腦下載版本。  
  
## <a name="include-subfolders"></a>包含子資料夾  
 指定將搜尋 [查詢] 資料夾的子資料夾。  
  
## <a name="find-options"></a>尋找選項  
 您可以展開或摺疊 [尋找選項] 區段。 可選取或清除下列選項：  
  
 大小寫須相符  
 選取時，[尋找結果] 搜尋會區分大小寫  
  
 全字拼寫須相符  
 選取時，[尋找結果] 視窗只會傳回全字拼寫相符的項目。  
  
 使用規則運算式  
 如果已選取此核取方塊，您可以使用特殊標記法來定義文字模式，以在 [尋找目標] 或 [取代為] 文字方塊中進行比對。 如需這些標記法的清單，請參閱[在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。  
  
 尋找下列檔案類型  
 這個清單可指定要在 [查詢] 目錄中搜尋的檔案類型。 如果此欄位空白，則會搜尋 [查詢] 目錄中的所有檔案。  
  
 選取此清單中的任一項目，即可輸入預先設定的搜尋字串，以尋找特定類型的檔案。  
  
## <a name="result-options"></a>結果選項  
 您可以展開或摺疊 [結果選項] 區段。 可選取或清除下列選項：  
  
 尋找結果 1 視窗  
 若選取此選項，目前搜尋的結果將會取代 [尋找結果 1] 視窗的內容。 這個視窗會自動開啟以顯示搜尋結果。 若要手動開啟此視窗，請從 [檢視] 功能表中選取 [其他視窗]，並選擇 [尋找結果 1]。  
  
 尋找結果 2 視窗  
 若選取此選項，目前搜尋的結果將會取代 [尋找結果 2] 視窗的內容。 這個視窗會自動開啟以顯示搜尋結果。 若要手動開啟此視窗，請從 [檢視] 功能表中選取 [其他視窗]，並選擇 [尋找結果 2]。  
  
 只顯示檔名  
 顯示含有符合搜尋內容的檔案清單，而非顯示搜尋符合項目本身。  
  
 附加結果  
 將此搜尋結果附加到上一個搜尋結果。  
  
## <a name="see-also"></a>請參閱  
 [尋找和取代文字](../ide/finding-and-replacing-text.md)   
 [檔案中取代](../ide/replace-in-files.md)   
 [Visual Studio 命令](../ide/reference/visual-studio-commands.md)
