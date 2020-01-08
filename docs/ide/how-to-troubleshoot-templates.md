---
title: 針對專案範本和項目範本載入進行疑難排解
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bef6a460f1a59823930597565b955b591ab48a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591381"
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

1. 解壓縮 *.zip* 檔。

1. 在 Visual Studio 的 [檔案] 功能表中選擇 [開啟] > [檔案]。

1. 選取範本的 *vstemplate* 檔案，然後選擇 [開啟]。

1. 確認 *vstemplate* 檔案的 XML 遵守範本結構描述。 如需 *vstemplate* 結構描述的詳細資訊，請參閱[範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。

    > [!NOTE]
    > 撰寫 *vstemplate* 檔案時若要取得 IntelliSense 支援，請在 `VSTemplate` 元素中新增 `xmlns` 屬性並為它指派 `http://schemas.microsoft.com/developer/vstemplate/2005` 值。

1. 儲存並關閉 *vstemplate* 檔案。

1. 選取要包含在範本中的檔案，按一下滑鼠右鍵，選擇 [Send to] (傳送至) > [壓縮的 (zipped) 資料夾]。 您選取的檔案即會壓縮成 *.zip* 檔。

1. 將新的 *.zip* 檔放在與舊 *.zip* 檔相同的目錄中。

1. 刪除已解壓縮的範本檔案和舊範本 *.zip* 檔案。

## <a name="enable-diagnostic-logging"></a>啟用診斷記錄

您可以遵循[針對範本探索進行疑難排解 (擴充性)](../extensibility/troubleshooting-template-discovery.md) 中的步驟來啟用範本探索的診斷記錄。

## <a name="see-also"></a>請參閱

- [針對範本探索進行疑難排解 (擴充性)](../extensibility/troubleshooting-template-discovery.md)
- [自訂範本](../ide/customizing-project-and-item-templates.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
