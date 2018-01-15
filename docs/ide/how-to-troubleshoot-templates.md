---
title: "針對 Visual Studio 專案範本和項目範本載入進行疑難排解 | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ba6d9a73cd45a0e497fb2ecc0f4b4697071e3b37
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-troubleshoot-templates"></a>如何：針對範本進行疑難排解

如果範本無法在開發環境中載入，有數種方式可找出問題。

## <a name="validate-the-vstemplate-file"></a>驗證 .vstemplate 檔案

如果範本中的 .vstemplate 檔案未遵守 Visual Studio 範本結構描述，範本可能不會出現在 [新增專案] 對話方塊中。

### <a name="to-validate-the-vstemplate-file"></a>驗證 .vstemplate 檔案

1. 找出包含樣板的.zip 檔。

1. 將 zip 檔解壓縮。

1. 在 Visual Studio 的 [檔案] 功能表中選擇 [開啟] > [檔案]。

1. 選取範本的 .vstemplate 檔案，然後選擇 [開啟]。

1. 確認 .vstemplate 檔案的 XML 遵守範本結構描述。 如需 .vstemplate 結構描述的詳細資訊，請參閱[範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。

    > [!NOTE]
    > 撰寫 .vstemplate 檔案時若要取得 IntelliSense 支援，請在 `VSTemplate` 項目中新增 `xmlns` 屬性並為它指派 http://schemas.microsoft.com/developer/vstemplate/2005 的值。

1. 儲存並關閉.vstemplate 檔案。

1. 選取要包含在範本中的檔案，按一下滑鼠右鍵，選擇 [Send to] (傳送至) > [壓縮的 (zipped) 資料夾]。 您選取的檔案即會壓縮成 .zip 檔。

1. 將新的 .zip 檔放在與舊 .zip 檔相同的目錄中。

1. 刪除已解壓縮的樣板檔案和舊樣板 .zip 檔案。

## <a name="monitor-the-event-log"></a>監視事件記錄檔

處理範本 .zip 檔案時遇到 Visual Studio 記錄錯誤。 如果 [新增專案] 對話方塊中未如預期顯示範本，您可以使用 [事件檢視器] 針對此問題進行疑難排解。

### <a name="to-locate-template-errors-in-event-viewer"></a>在事件檢視器中找出範本錯誤

1. 在 Windows 中，從 [開始] 功能表中選擇 [Windows 系統管理工具] > [事件檢視器]。

1. 在左窗格中，選擇 [Windows 記錄檔] > [應用程式]。

1. 尋找 **Source** 值為 `Visual Studio - VsTemplate` 的事件。

1. 若要檢視錯誤，請按兩下範本事件。

## <a name="enable-diagnostic-logging"></a>啟用診斷記錄

您可以遵循[針對範本探索 (擴充性) 進行疑難排解](../extensibility/troubleshooting-template-discovery.md)中的步驟來啟用範本探索的診斷記錄。

## <a name="see-also"></a>另請參閱

[針對範本探索 (擴充性) 進行疑難排解](../extensibility/troubleshooting-template-discovery.md)  
[自訂範本](../ide/customizing-project-and-item-templates.md)  
[建立專案和項目範本](../ide/creating-project-and-item-templates.md)  
[範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)