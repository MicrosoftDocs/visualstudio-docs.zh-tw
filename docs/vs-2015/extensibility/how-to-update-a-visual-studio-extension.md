---
title: 更新擴充功能 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0d1464cdd2be79cd93a3e98bcf8769e8f4b8b89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840207"
---
# <a name="how-to-update-a-visual-studio-extension"></a>如何︰更新 Visual Studio 擴充功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 **擴充功能和更新** 來更新系統上的 Visual Studio 延伸模組，以安裝更新的版本。 如果您建立了擴充功能的更新版本，您可以在 VSIX 資訊清單中遞增版本號碼，以表示更新的版本。

 當內送延伸模組的 VSIX 資訊清單與 `ID` 已安裝的版本和較高的數位相同時，就會安裝更新 `Version` 。 如果 `Version` 數位相同或更低，則無法安裝封裝。 如果 `ID` 值不相符，尚未安裝的套件會被辨識為個別的副檔名。

 為了避免在開發期間發生衝突，建議您卸載舊版的延伸模組，同時卸載或停用任何其他可能發生衝突的延伸模組。

### <a name="to-update-an-extension-on-your-system"></a>在您的系統上更新擴充功能

1. 在 [工具] 功能表上，按一下 [延伸模組與更新]。

2. 在左窗格中，按一下 [ **更新**]。

3. 在中間窗格中，按一下您要安裝的更新。

     更新的延伸模組的版本號碼會顯示在右窗格中，以及其他資訊。

4. 按一下右窗格底部的 [ **更新**]。

### <a name="to-publish-an-update-of-an-extension"></a>發佈延伸模組的更新

1. 在 Visual Studio 中，開啟您想要更新之延伸模組的解決方案。 進行變更。

    > [!IMPORTANT]
    > 未簽署的所有使用者延伸模組不會自動更新。 您應一律簽署您的延伸模組。

2. 在 **方案總管**中，開啟 [副檔名]。

3. 在 [資訊清單設計工具] 中，增加 [ **版本** ] 欄位中的數位值。

4. 儲存並建立解決方案。

5. 將專案) 之 \bin\Debug\ 資料夾中的新 .vsix 檔 (上傳至 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 的網站。

     當具有舊版擴充功能的使用者開啟 [ **擴充功能和更新**] 時，新版本將會出現在 [ **更新** ] 清單中，前提是該工具已設定為自動尋找更新。

     您可以在 [**更新**] 窗格底部啟用或停用自動檢查更新， (**啟用/停用可用更新的自動偵測**) ，變更 [**工具/選項/環境/擴充功能和更新**] 中的 [**檢查更新**] 設定。

    > [!NOTE]
    > 從 Visual Studio 2015 Update 2 開始，您可以指定 (在 [工具] / [選項] / [環境] / [延伸模組和更新]**** 中) 是否要自動更新每個使用者延伸模組、所有使用者延伸模組，或兩者皆自動更新 (預設值)。

## <a name="see-also"></a>另請參閱
 [尋找和使用 Visual Studio 擴充](../ide/finding-and-using-visual-studio-extensions.md)功能[的 VSIX 封裝剖析](../extensibility/anatomy-of-a-vsix-package.md)
