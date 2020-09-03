---
title: 檔案中取代 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001f1faa969275788b10bc9bd1e6398373a54b37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669966"
---
# <a name="replace-in-files"></a>檔案中取代
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[檔案中取代]** 可讓您在一組指定檔案中搜尋程式碼的字串或運算式，並變更部分或所有找到的相符項目。 找到的相符專案與所採取的動作會列在 [**結果選項**] 中所選取的 [**尋找結果**] 視窗中。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

 您可以使用下列方法之一，在 [檔案中尋找]**** 視窗中顯示 [檔案中取代]****。

### <a name="to-display-replace-in-files"></a>若要顯示檔案中取代

1. 在 [編輯]**** 功能表上，展開 [尋找和取代]****。

2. 選擇 [檔案中取代]****。

     — 或者—

     如果 [尋找和取代]**** 視窗已開啟，請選擇工具列中的 [檔案中取代]****。

## <a name="find-what"></a>尋找目標
 若要搜尋新的文字字串或運算式，請在方塊中指定。 若要搜尋您最近搜尋過的 20 筆字串之一，請開啟該清單，並選擇您要搜尋的字串。 如果您想要在搜尋字串中使用一或多個規則運算式，請選擇相鄰的 [運算式產生器]**** 按鈕。 如需詳細資訊，請參閱[在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。

## <a name="replace-with"></a>取代為
 若要將 [尋找目標]**** 方塊中的字串執行個體取代為其他字串，請在 [取代為]**** 方塊中輸入取代字串。 若要刪除 [尋找目標]**** 方塊中的字串執行個體，請將此欄位保留空白。 開啟清單即可顯示您最近搜尋的 20 筆字串。 如果您想要在取代字串中使用一或多個規則運算式，請選擇相鄰的 [運算式產生器]**** 按鈕。 如需詳細資訊，請參閱[在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。

## <a name="look-in"></a>查詢
 您從 [查詢]**** 下拉式清單中選擇的選項，可決定 [檔案中取代]**** 僅搜尋目前使用中的檔案，或搜尋儲存在特定資料夾中的所有檔案。 從清單中選取搜尋範圍、輸入資料夾路徑，或按一下 [瀏覽 (...)]**** 按鈕，顯示 [選擇搜尋資料夾]**** 對話方塊，然後選擇要搜尋的資料夾集合。 您也可以直接在 [查詢]**** 方塊中輸入路徑。

> [!NOTE]
> 如果選取 [查詢]**** 選項時，所搜尋的檔案已從原始程式碼控制簽出，則只會搜尋該檔案的本機電腦下載版本。

## <a name="find-options"></a>尋找選項
 您可以展開或折迭 [ **尋找選項** ] 區段。 可選取或清除下列選項：

 選取 [尋找結果] 視窗時，[ **尋找結果** ] 視窗只會顯示內容和大小寫兩者相符的 [ **尋找目標** ] 字串實例。 例如，若搜尋 "MyObject" 時選取 [大小寫須相符]****，則會傳回 "MyObject"，而不是 "myobject" 或 "MYOBJECT"。

 選取 [尋找結果] 視窗時，[ **尋找結果** ] 視窗只會顯示完整文字中相符的 [ **尋找目標** ] 字串實例。 例如，搜尋 "MyObject" 時會傳回 "MyObject"，而不是 "CMyObject" 或 "MyObjectC"。

 如果選取此核取方塊，請使用正則運算式，您可以使用特殊標記法來定義 [ **尋找目標** ] 或 [ **取代成** ] 文字方塊中的文字模式。 如需這些標記法的清單，請參閱[在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。

 查看這些檔案類型此清單指出要在 [ **查詢** ] 目錄中搜尋的檔案類型。 如果此欄位保持空白，則會搜尋 [查詢]**** 目錄中的所有檔案。

 選取此清單中的任一項目，即可輸入預先設定的搜尋字串，以尋找特定類型的檔案。

## <a name="result-options"></a>結果選項
 您可以展開或折迭 [ **結果選項** ] 區段。 可選取或清除下列選項：

 當選取 [結果 1] 視窗時，目前搜尋的結果將會取代 [ **尋找結果 1** ] 視窗的內容。 此視窗會自動開啟，以顯示您的搜尋結果。 若要手動開啟此視窗，請從 [檢視]**** 功能表中選取 [其他視窗]****，並選擇 [尋找結果 1]****。

 當選取 [結果 2] 視窗時，目前搜尋的結果將會取代 [ **尋找結果 2** ] 視窗的內容。 此視窗會自動開啟，以顯示您的搜尋結果。 若要手動開啟此視窗，請從 [檢視]**** 功能表中選取 [其他視窗]****，並選擇 [尋找結果 2]****。

 只有在選取此核取方塊時才顯示檔案名，[尋找結果] 視窗會列出包含搜尋字串之所有檔案的完整名稱和路徑。 不過，這些結果不含字串出現位置的程式碼行。 此核取方塊僅在 [檔案中尋找] 中提供。

 當您選取 [全部取代] 之後，請將修改過的檔案保持開啟狀態，並將所有已進行取代的檔案保持開啟，以便您可以復原或儲存變更。 記憶體的容量可能會限制進行取代作業之後，能夠保持開啟的檔案數目。

> [!CAUTION]
> 您僅能針對仍然保持開啟以供編輯的檔案執行 [恢復] 動作。 如果沒有選取此選項，沒有開啟以供編輯的檔案將會保持關閉狀態，且該些檔案就無法使用 [恢復]**** 選項。

## <a name="see-also"></a>另請參閱
 [尋找和取代](../ide/finding-and-replacing-text.md)檔案 [中的文字尋找](../ide/find-in-files.md) [Visual Studio 命令](../ide/reference/visual-studio-commands.md)
