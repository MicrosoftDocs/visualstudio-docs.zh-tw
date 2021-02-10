---
title: 檔案中尋找
description: 瞭解「檔案中尋找」功能，以及如何使用它來搜尋一組特定的檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b04853681ef764d494f16df4659acbbec0bdd018
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945600"
---
# <a name="find-in-files"></a>檔案中尋找

[檔案中尋找] 可讓您搜尋一組指定的檔案。 找到的相符專案與所採取的動作會列在 [**結果選項**] 中所選取的 [**尋找結果**] 視窗中。

您可以使用下列任何方法，以在 [尋找和取代] 視窗中顯示 [檔案中尋找]。

## <a name="to-display-find-in-files"></a>顯示檔案中尋找

1. 在功能表列上，選擇 [**編輯**  >  **尋找和取代**]。

1. 選擇 [檔案中尋找]。

若要取消尋找作業，請按下 **Ctrl**  +  **Break**。

> [!NOTE]
> [尋找和取代] 工具不會使用 `Hidden` 或 `System` 屬性來搜尋目錄。

## <a name="find-what"></a>尋找目標

若要搜尋新的文字字串或運算式，請在方塊中指定。 若要搜尋您最近搜尋過的 20 個字串之一，請開啟下拉式清單，然後選擇字串。 如果您想要在搜尋字串中使用一或多個規則運算式，請選擇相鄰的 [運算式產生器] 按鈕。 如需詳細資訊，請參閱 [在 Visual Studio 中使用正則運算式](../ide/using-regular-expressions-in-visual-studio.md)。

> [!NOTE]
> 只有在選取 [尋找選項] 下方的 [使用規則運算式] 時，才會啟用 [運算式產生器] 按鈕。

## <a name="look-in"></a>查詢

從 [查詢] 下拉式清單中選擇的選項會決定 [檔案中尋找] 僅搜尋目前使用中的檔案，或搜尋儲存在特定資料夾中的所有檔案。 從清單中選取搜尋範圍，或按一下 [瀏覽 (...)] 按鈕，顯示 [選擇搜尋資料夾] 對話方塊，然後輸入您本身的目錄集。 您也可以直接在 [查詢] 方塊中輸入路徑。

> [!WARNING]
> 使用 [整個方案] 或 [目前專案] 選項時，並不會搜尋專案和方案檔。 如果您想查詢專案檔，請選擇搜尋資料夾。

> [!NOTE]
> 如果選取 [查詢] 選項時，所搜尋的檔案已從原始程式碼控制簽出，則只會搜尋該檔案的本機電腦下載版本。

## <a name="include-subfolders"></a>包含子資料夾

指定將搜尋 [查詢] 資料夾的子資料夾。

## <a name="find-options"></a>尋找選項

您可以展開或折迭 [ **尋找選項** ] 區段。 可選取或清除下列選項：

**大小寫須相符**

選取時，[尋找結果] 搜尋會區分大小寫

**全字拼寫須相符**

選取時，[尋找結果] 視窗只會傳回全字拼寫相符的項目。

**使用正則運算式**

如果已選取此核取方塊，您可以使用特殊標記法來定義文字模式，以在 [尋找目標] 或 [取代為] 文字方塊中進行比對。 如需這些標記法的清單，請參閱 [在 Visual Studio 中使用正則運算式](../ide/using-regular-expressions-in-visual-studio.md)。

**尋找下列檔案類型**

這個清單可指定要在 [查詢] 目錄中搜尋的檔案類型。 如果此欄位空白，則會搜尋 [查詢] 目錄中的所有檔案。

選取此清單中的任一項目，即可輸入預先設定的搜尋字串，以尋找特定類型的檔案。

## <a name="result-options"></a>結果選項

您可以展開或折迭 [ **結果選項** ] 區段。 可選取或清除下列選項：

**尋找結果1視窗**

若選取此選項，目前搜尋的結果將會取代 [尋找結果 1] 視窗的內容。 此視窗會自動開啟，以顯示您的搜尋結果。 若要手動開啟此視窗，請從 [檢視] 功能表中選取 [其他視窗]，並選擇 [尋找結果 1]。

**尋找結果2視窗**

若選取此選項，目前搜尋的結果將會取代 [尋找結果 2] 視窗的內容。 此視窗會自動開啟，以顯示您的搜尋結果。 若要手動開啟此視窗，請從 [檢視] 功能表中選取 [其他視窗]，並選擇 [尋找結果 2]。

**僅顯示檔案名稱**

顯示含有符合搜尋內容的檔案清單，而非顯示搜尋符合項目本身。

**附加結果**

將此搜尋結果附加到上一個搜尋結果。

## <a name="see-also"></a>另請參閱

- [尋找和取代文字](../ide/finding-and-replacing-text.md)
- [檔案中取代](../ide/replace-in-files.md)
- [Visual Studio 命令](../ide/reference/visual-studio-commands.md)