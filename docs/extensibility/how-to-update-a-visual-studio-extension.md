---
title: 如何：更新 Visual Studio 延伸模組 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee81fe30e10253239bc51dd9d2f199340debc65a
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905618"
---
# <a name="how-to-update-a-visual-studio-extension"></a>如何：更新 Visual Studio 延伸模組
您可以使用 [**擴充功能和更新**] 來安裝更新的版本，以更新系統上的 Visual Studio 延伸模組。 如果您建立擴充功能的更新版本，您可以在 VSIX 資訊清單中遞增版本號碼，將其表示為已更新。

 當內送擴充功能的 VSIX 資訊清單與 `ID` 已安裝的版本和較高的數位相同時，就會安裝更新 `Version` 。 如果此 `Version` 數目相同或較低，則無法安裝封裝。 如果 `ID` 值不相符，則尚未安裝的封裝會被辨識為個別的延伸模組。

 為協助防止開發期間發生衝突，建議您卸載舊版的延伸模組，並同時卸載或停用任何其他可能衝突的延伸模組。

## <a name="to-update-an-extension-on-your-system"></a>更新系統上的延伸模組

1. 在 [工具] **** 功能表上，按一下 [擴充功能和更新] ****。

2. 在左窗格中，按一下 [**更新**]。

3. 在中間窗格中，按一下您想要安裝的更新。

     更新延伸模組的版本號碼會顯示在右窗格中，以及其他資訊。

4. 在右窗格底部，按一下 [**更新**]。

## <a name="to-publish-an-update-of-an-extension"></a>發行延伸模組的更新

1. 在 Visual Studio 中，開啟您想要更新之延伸模組的解決方案。 進行變更。

    > [!IMPORTANT]
    > 不帶正負號的所有使用者延伸模組不會自動更新。 您應該一律簽署您的延伸模組。

2. 在**方案總管**中，開啟*來源. 副檔名 .manifest*。

3. 在 [資訊清單設計工具] 中，增加 [**版本**] 欄位中的數位值。

4. 儲存方案並加以建立。

5. 將新的 *.vsix*檔案（位於專案的 * \bin\Debug \* 資料夾）上傳至[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)網站。

     當具有舊版延伸模組的使用者開啟 [**擴充功能和更新**] 時，如果工具設定為 [自動尋找更新]，新版本將會出現在 [**更新**] 清單中。

     您可以在 [**工具** **] [選項] [** 環境延伸模組**Check for updates**和更新] 中，啟用或停用 [更新] 窗格底部的 [自動檢查更新] （**啟用/停用可用更新的自動偵測**）  >  **Options**  >  **Environment**  >  ** **。

    > [!NOTE]
    > 從 Visual Studio 2015 Update 2 開始，您可以指定（在 [**工具**] [選項] [環境] [  >  **Options**  >  **Environment**  >  **擴充功能和更新**] 中）是否要自動更新每個使用者的延伸模組、所有使用者延伸模組或兩者（預設設定）。

## <a name="see-also"></a>另請參閱
- [VSIX 封裝的剖析](../extensibility/anatomy-of-a-vsix-package.md)
- [尋找及使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)
