---
title: 為 Windows 安裝程式部署準備擴展 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8636dfbbad06192e5edbb61a9a784f64b8f3f14f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702020"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>在 Windows 安裝程式部署準備擴充
不能使用 Windows 安裝程式套件 (MSI) 部署 VSIX 套件。 但是,您可以提取用於 MSI 部署的 VSIX 包的內容。 本文件展示如何準備預設輸出為 VSIX 套件的專案,以便包含在安裝程式專案中。

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>在 Windows 安裝程式部署準備擴充項目
 在添加到安裝程式專案之前,對新的擴展專案執行這些步驟。

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>在 Windows 安裝程式部署準備擴充項目

1. 創建 VSPackage、MEF 元件、編輯器修飾或其他包含 VSIX 清單的擴充性項目類型。

2. 開啟代碼編輯器中的 VSIX 清單。

3. 將`InstalledByMsi`VSIX 清單的元素`true`設定為 。 有關 VSIX 清單的詳細資訊,請參閱[VSIX 擴充架構 2.0 參考](../extensibility/vsix-extension-schema-2-0-reference.md)。

     這可以防止 VSIX 安裝程式嘗試安裝元件。

4. 右鍵單擊**解決方案資源管理器**中的專案,然後單擊 **"屬性**"。

5. 選擇**VSIX**選項卡。

6. 選中標記為將**VSIX 內容複製到以下位置**的框,然後鍵入安裝程式專案將拾取檔的路徑。

## <a name="extract-files-from-an-existing-vsix-package"></a>從現有 VSIX 套件中提取檔案
 執行這些步驟,在沒有源檔時,將現有 VSIX 包的內容添加到安裝程式專案中。

### <a name="to-extract-files-from-an-existing-vsix-package"></a>從現有 VSIX 套件中提取檔案

1. 重新命名 *。包含*從*檔案名.vsix*到*filename.zip*的副檔名的 VSIX 檔。

2. 將 *.zip*檔案的內容複製到目錄中。

3. 從目錄中移除 *[Content_types]xml*檔。

4. 編輯 VSIX 清單,如上一過程所示。

5. 將其餘檔添加到安裝程式專案中。

## <a name="see-also"></a>另請參閱
- [視覺化工作室安裝程式部署](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [演練:建立自訂操作](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))
