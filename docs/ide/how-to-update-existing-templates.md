---
title: 更新現有的專案項目範本
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b5f72f6cbe2fcf3be2566fd7e51d7366dd2563ae
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985886"
---
# <a name="how-to-update-existing-templates"></a>HOW TO：更新現有範本

在建立範本並將檔案壓縮成 *.zip* 檔之後，建議您修改範本。 若要執行此動作，您可以手動變更範本中的檔案，或從以範本為基礎的專案中匯出新範本。

## <a name="using-the-export-template-wizard-to-update-an-existing-project-template"></a>使用 [匯出範本精靈] 更新現有的專案範本

Visual Studio 提供可用來更新現有範本的 [匯出範本精靈]：

1. 開啟 [新增專案] 對話方塊，方法是選擇 [檔案] > [新增] > [專案]。

1. 選取您想要更新的範本，輸入專案的名稱和位置，然後選擇 [確定]。

1. 在 Visual Studio 中修改專案。

1. 選擇 [專案] 功能表上的 [匯出範本]。

    [匯出範本精靈] 隨即開啟。

1. 遵循精靈中的指示，將範本匯出成 *.zip* 檔案。

1. (選擇性) 若要將範本新增至 [新增專案] 對話方塊，請將 *.zip* 檔案放在下列目錄中：*%USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ProjectTemplates*。 如果未在 [匯出範本精靈] 選取 [自動將範本匯入 Visual Studio] 選項，即必須執行此步驟。

1. 刪除舊的範本 *.zip* 檔案。

## <a name="manually-update-an-existing-template"></a>手動更新現有範本

修改壓縮的 *.zip* 檔中的檔案，即可不使用 [匯出範本精靈] 來更新現有範本。

### <a name="to-manually-update-an-existing-template"></a>手動更新現有範本

1. 尋找包含範本的 *.zip* 檔。 使用者專案範本位在 *%USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ProjectTemplates*。

1. 解壓縮 *.zip* 檔。

1. 修改或刪除目前的範本檔，或將新檔案加入至範本。

1. 開啟、修改和儲存 *.vstemplate* XML 檔，以處理更新的行為或新檔案。

    如需 *.vstemplate* 結構描述的詳細資訊，請參閱 [Visual Studio 範本結構描述參考 (擴充性)](../extensibility/visual-studio-template-schema-reference.md)。 如需您可以在來源檔案中參數化哪些項目的詳細資訊，請參閱[範本參數](../ide/template-parameters.md)。

1. 在範本中選取檔案，按一下滑鼠右鍵或從操作功能表中選擇 [Send to] (傳送至) > [壓縮的 (zipped) 資料夾]。

    您選取的檔案即會壓縮成 *.zip* 檔。

1. 將新的 *.zip* 檔放在與舊 *.zip* 檔相同的目錄中。

1. 刪除已解壓縮的範本檔案和舊範本 *.zip* 檔案。

## <a name="see-also"></a>另請參閱

- [自訂範本](../ide/customizing-project-and-item-templates.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [範本參數](../ide/template-parameters.md)