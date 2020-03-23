---
title: 更新現有的專案項目範本
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 44f99646330d3c8a75bd94310bc0adf9073f9d49
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591355"
---
# <a name="how-to-update-existing-templates"></a>如何：更新現有的範本

在建立範本並將檔案壓縮成 *.zip* 檔之後，建議您修改範本。 若要執行此動作，您可以手動變更範本中的檔案，或從以範本為基礎的專案中匯出新範本。

## <a name="use-the-export-template-wizard"></a>使用 [匯出範本精靈]

Visual Studio 提供可用來更新現有範本的 [匯出範本精靈]****：

1. **從功能表**欄中選擇 **"檔** > **新專案** > "。

1. 選取您想要更新的範本，然後繼續建立新專案的步驟。

1. 在 Visual Studio 中修改專案。 例如，變更輸出類型，或將新檔案新增至專案。

1. 在 **"專案**"功能表上，選擇 **"匯出範本**"。

    將打開 **"匯出範本嚮導**"。

1. 遵循精靈中的指示，將範本匯出成 *.zip* 檔案。

1. (選擇性) 將 *.zip* 檔案放在下列目錄中：*%USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ProjectTemplates* 以供選取。 如果未在 [匯出範本精靈]**** 選取 [自動將範本匯入 Visual Studio]**** 選項，即必須執行此步驟。

1. 刪除舊的範本 *.zip* 檔案。

## <a name="manually-update-an-existing-template"></a>手動更新現有範本

修改壓縮的 *.zip* 檔中的檔案，即可不使用 [匯出範本精靈]**** 來更新現有範本。

### <a name="to-manually-update-an-existing-template"></a>手動更新現有範本

1. 尋找包含範本的 *.zip* 檔。 使用者專案範本位在 *%USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ProjectTemplates*。

1. 提取 *.zip*檔。

1. 修改或刪除目前的範本檔，或將新檔案加入至範本。

1. 開啟、修改和儲存 *.vstemplate* XML 檔，以處理更新的行為或新檔案。

    如需 *.vstemplate* 結構描述的詳細資訊，請參閱 [Visual Studio 範本結構描述參考 (擴充性)](../extensibility/visual-studio-template-schema-reference.md)。 如需您可以在來源檔案中參數化哪些項目的詳細資訊，請參閱[範本參數](../ide/template-parameters.md)。

1. 選擇範本中的檔，然後從按右鍵或內容功能表中選擇"**發送到** > **壓縮（壓縮）"資料夾**。

    您選擇的檔將壓縮到 *.zip*檔中。

1. 將新的 *.zip* 檔放在與舊 *.zip* 檔相同的目錄中。

1. 刪除提取的範本檔和舊的範本 *.zip*檔。

## <a name="see-also"></a>另請參閱

- [自訂範本](../ide/customizing-project-and-item-templates.md)
- [創建專案和專案範本](../ide/creating-project-and-item-templates.md)
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [範本參數](../ide/template-parameters.md)
