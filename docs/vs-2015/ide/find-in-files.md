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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e21d0880813452e37c9e20afdc98321e4b2e3a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655907"
---
# <a name="find-in-files"></a>檔案中尋找
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[檔案中尋找]** 可讓您搜尋一組指定的檔案。 找到的相符專案與所採取的動作會列在 [**結果選項**] 中所選取的 [**尋找結果**] 視窗中。

 您可以使用下列任何方法，以在 [尋找和取代]**** 視窗中顯示 [檔案中尋找]****。

### <a name="to-display-find-in-files"></a>顯示檔案中尋找

1. 在功能表列上，依序選擇 [編輯]**** 和 [尋找和取代]****。

2. 選擇 [檔案中尋找]****。

   若要取消尋找作業，請按 CTRL + BREAK。

> [!NOTE]
> [尋找和取代] 工具不會搜尋目錄與 `Hidden` 或 `System` 屬性集。

## <a name="find-what"></a>尋找目標
 若要搜尋新的文字字串或運算式，請在方塊中指定。 若要搜尋您最近搜尋過的 20 筆字串之一，請開啟該清單，並選擇您要搜尋的字串。 如果您想要在搜尋字串中使用一或多個規則運算式，請選擇相鄰的 [運算式產生器]**** 按鈕。 如需詳細資訊，請參閱[在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。

## <a name="look-in"></a>查詢
 從 [查詢]**** 下拉式清單中選擇的選項會決定 [檔案中尋找]**** 僅搜尋目前使用中的檔案，或搜尋儲存在特定資料夾中的所有檔案。 從清單中選取搜尋範圍，或按一下 [瀏覽 (...)]**** 按鈕，顯示 [選擇搜尋資料夾]**** 對話方塊，然後輸入您本身的目錄集。 您也可以直接在 [查詢]**** 方塊中輸入路徑。

> [!WARNING]
> 使用 [整個方案]**** 或 [目前專案]**** 選項時，並不會搜尋專案和方案檔。 如果您想查詢專案檔，請選擇搜尋資料夾。

> [!NOTE]
> 如果選取 [查詢]**** 選項時，所搜尋的檔案已從原始程式碼控制簽出，則只會搜尋該檔案的本機電腦下載版本。

## <a name="include-subfolders"></a>包含子資料夾
 指定將搜尋 [查詢]**** 資料夾的子資料夾。

## <a name="find-options"></a>尋找選項
 您可以展開或折迭 [ **尋找選項** ] 區段。 可選取或清除下列選項：

 選取的相符案例， **尋找結果** 搜尋會區分大小寫

 當選取時，[ **尋找結果** ] 視窗只會傳回全字相符專案，以符合全字組。

 如果選取此核取方塊，請使用正則運算式，您可以使用特殊標記法來定義要在 [ **尋找目標** ] 或 [ **取代成** ] 文字方塊中比對的文字模式。 如需這些標記法的清單，請參閱[在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。

 查看這些檔案類型此清單指出要在 [ **查詢** ] 目錄中搜尋的檔案類型。 如果此欄位空白，則會搜尋 [查詢]**** 目錄中的所有檔案。

 選取此清單中的任一項目，即可輸入預先設定的搜尋字串，以尋找特定類型的檔案。

## <a name="result-options"></a>結果選項
 您可以展開或折迭 [ **結果選項** ] 區段。 可選取或清除下列選項：

 當選取 [結果 1] 視窗時，目前搜尋的結果將會取代 [ **尋找結果 1** ] 視窗的內容。 此視窗會自動開啟，以顯示您的搜尋結果。 若要手動開啟此視窗，請從 [檢視]**** 功能表中選取 [其他視窗]****，並選擇 [尋找結果 1]****。

 當選取 [結果 2] 視窗時，目前搜尋的結果將會取代 [ **尋找結果 2** ] 視窗的內容。 此視窗會自動開啟，以顯示您的搜尋結果。 若要手動開啟此視窗，請從 [檢視]**** 功能表中選取 [其他視窗]****，並選擇 [尋找結果 2]****。

 顯示檔案名只會顯示包含搜尋相符專案的檔案清單，而不是顯示搜尋相符專案。

 附加結果會將搜尋結果附加至先前的搜尋結果。

## <a name="see-also"></a>另請參閱
 [尋找和取代](../ide/finding-and-replacing-text.md)檔案[Visual Studio 命令](../ide/reference/visual-studio-commands.md)[中的文字取代](../ide/replace-in-files.md)
