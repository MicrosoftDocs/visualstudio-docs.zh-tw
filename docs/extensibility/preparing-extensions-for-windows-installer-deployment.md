---
title: 準備 Windows Installer 部署的擴充功能 |Microsoft Docs
description: 瞭解如何準備專案，其預設輸出為要包含在安裝專案中的 VSIX 套件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6436d05d3b15be1c1fe8d7c7bb9c8592dee091dc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090274"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>準備 Windows Installer 部署的擴充功能
您無法使用 Windows Installer 套件 (MSI) 來部署 VSIX 套件。 不過，您可以解壓縮適用于 MSI 部署的 VSIX 套件內容。 本檔將說明如何準備專案，其預設輸出為 VSIX 封裝，以包含在安裝專案中。

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>準備 Windows Installer 部署的擴充功能專案
 請在新的擴充功能專案上執行這些步驟，再新增至安裝專案。

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>準備擴充專案以進行 Windows Installer 部署

1. 建立 VSPackage、MEF 元件、編輯器裝飾或其他包含 VSIX 資訊清單的擴充性專案類型。

2. 在程式碼編輯器中開啟 VSIX 資訊清單。

3. 將 `InstalledByMsi` VSIX 資訊清單的元素設定為 `true` 。 如需 VSIX 資訊清單的詳細資訊，請參閱 [vsix 延伸架構2.0 參考](../extensibility/vsix-extension-schema-2-0-reference.md)。

     這可防止 VSIX 安裝程式嘗試安裝元件。

4. 以滑鼠右鍵按一下 **方案總管** 中的專案，然後按一下 [ **屬性**]。

5. 選取 [ **VSIX** ] 索引標籤。

6. 核取標示 [ **將 VSIX 內容複寫到下列位置** ] 的方塊，並輸入安裝專案將在其中挑選檔案的路徑。

## <a name="extract-files-from-an-existing-vsix-package"></a>從現有的 VSIX 封裝解壓縮檔案
 當您沒有原始程式檔時，請執行下列步驟，將現有 VSIX 套件的內容加入至安裝專案。

### <a name="to-extract-files-from-an-existing-vsix-package"></a>從現有的 VSIX 封裝解壓縮檔案

1. 重新命名 *。VSIX* 檔案，其中包含從 *檔案名 .vsix* 到 *filename.zip* 的副檔名。

2. 將 *.zip* 檔的內容複寫到目錄中。

3. 刪除目錄中的 *[Content_types] .xml* 檔案。

4. 編輯 VSIX 資訊清單，如先前的程式所示。

5. 將其餘的檔案新增至您的安裝專案。

## <a name="see-also"></a>另請參閱
- [Visual Studio 安裝程式部署](/previous-versions/2kt85ked(v=vs.120))
- [逐步解說：建立自訂動作](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))