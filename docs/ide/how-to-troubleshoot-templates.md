---
title: 針對專案範本和專案範本進行疑難排解
description: 瞭解如何在範本無法于開發環境中載入時進行疑難排解。
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 842e34ce18767f5d16cc55d16b8346369fe6cef9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869111"
---
# <a name="how-to-troubleshoot-templates"></a>如何：針對範本進行疑難排解

如果範本無法在開發環境中載入，有數種方式可找出問題。

## <a name="validate-the-vstemplate-file"></a>驗證 vstemplate 檔案

::: moniker range="vs-2017"

如果範本中的 *vstemplate* 檔案未遵守 Visual Studio 範本結構描述，範本可能不會出現在 [新增專案] 對話方塊中。

::: moniker-end

::: moniker range=">=vs-2019"

如果範本中的 *vstemplate* 檔案未遵守 Visual Studio 範本結構描述，範本可能不會出現在您建立新專案的對話方塊中。

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>驗證 vstemplate 檔案

1. 尋找包含範本的 *.zip* 檔。

1. 將 *.zip* 檔案解壓縮。

1. 在 Visual Studio 的 [檔案] 功能表中選擇 [開啟] > [檔案]。

1. 選取範本的 *vstemplate* 檔案，然後選擇 [開啟]。

1. 確認 *vstemplate* 檔案的 XML 遵守範本結構描述。 如需 *vstemplate* 結構描述的詳細資訊，請參閱 [範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。

    > [!NOTE]
    > 撰寫 *vstemplate* 檔案時若要取得 IntelliSense 支援，請在 `VSTemplate` 元素中新增 `xmlns` 屬性並為它指派 `http://schemas.microsoft.com/developer/vstemplate/2005` 值。

1. 儲存並關閉 *vstemplate* 檔案。

1. 選取範本中包含的檔案、按一下滑鼠右鍵，然後選擇 [**傳送到**  >  **壓縮 (壓縮的) 資料夾**。 您選取的檔案會壓縮成 *.zip* 檔案。

1. 將新的 *.zip* 檔案放在與舊 *.zip* 檔相同的目錄中。

1. 刪除已解壓縮的範本檔案和舊的範本 *.zip* 檔。

## <a name="enable-diagnostic-logging"></a>啟用診斷記錄

您可以遵循[針對範本探索進行疑難排解 (擴充性)](../extensibility/troubleshooting-template-discovery.md) 中的步驟來啟用範本探索的診斷記錄。

## <a name="see-also"></a>另請參閱

- [針對範本探索進行疑難排解 (擴充性)](../extensibility/troubleshooting-template-discovery.md)
- [自訂範本](../ide/customizing-project-and-item-templates.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
