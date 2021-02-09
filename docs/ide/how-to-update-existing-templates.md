---
title: 更新現有的專案項目範本
description: 瞭解如何使用匯出範本嚮導和其他手動程式來更新您已經建立的專案專案範本。
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 12005ce6c280a828aa59c281803cb431cc08587a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869085"
---
# <a name="how-to-update-existing-templates"></a>如何：更新現有的範本

在建立範本並將檔案壓縮成 *.zip* 檔之後，建議您修改範本。 若要執行此動作，您可以手動變更範本中的檔案，或從以範本為基礎的專案中匯出新範本。

## <a name="use-the-export-template-wizard"></a>使用 [匯出範本精靈]

Visual Studio 提供可用來更新現有範本的 [匯出範本精靈]：

1. 從功能表列 **選擇 [** 檔案  >  **新**  >  **專案**]。

1. 選取您想要更新的範本，然後繼續建立新專案的步驟。

1. 在 Visual Studio 中修改專案。 例如，變更輸出類型，或將新檔案新增至專案。

1. 選擇 [ **專案** ] 功能表上的 [ **匯出範本**]。

    [ **匯出範本]** 隨即開啟。

1. 遵循精靈中的指示，將範本匯出成 *.zip* 檔案。

1.  (選擇性) 將 *.zip* 檔案放在下列目錄中： *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ProjectTemplates* ，使其可供選取。 如果未在 [匯出範本精靈] 選取 [自動將範本匯入 Visual Studio] 選項，即必須執行此步驟。

1. 刪除舊的範本 *.zip* 檔案。

## <a name="manually-update-an-existing-template"></a>手動更新現有範本

修改壓縮的 *.zip* 檔中的檔案，即可不使用 [匯出範本精靈] 來更新現有範本。

### <a name="to-manually-update-an-existing-template"></a>手動更新現有範本

1. 尋找包含範本的 *.zip* 檔。 使用者專案範本位於 *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ProjectTemplates*。

1. 將 *.zip* 檔案解壓縮。

1. 修改或刪除目前的範本檔，或將新檔案加入至範本。

1. 開啟、修改和儲存 *.vstemplate* XML 檔，以處理更新的行為或新檔案。

    如需 *.vstemplate* 結構描述的詳細資訊，請參閱 [Visual Studio 範本結構描述參考 (擴充性)](../extensibility/visual-studio-template-schema-reference.md)。 如需您可以在來源檔案中參數化哪些項目的詳細資訊，請參閱[範本參數](../ide/template-parameters.md)。

1. 在您的範本中選取檔案，然後從滑鼠右鍵功能表或操作功能表中選擇 [**傳送到**  >  **壓縮的 (壓縮的) 資料夾**。

    您選取的檔案會壓縮成 *.zip* 檔案。

1. 將新的 *.zip* 檔放在與舊 *.zip* 檔相同的目錄中。

1. 刪除已解壓縮的範本檔案和舊的範本 *.zip* 檔。

## <a name="see-also"></a>另請參閱

- [自訂範本](../ide/customizing-project-and-item-templates.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [範本參數](../ide/template-parameters.md)
