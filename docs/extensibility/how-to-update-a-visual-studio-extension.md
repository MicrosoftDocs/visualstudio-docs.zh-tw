---
title: 如何:更新視覺工作室擴展 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 266c0a49db1bca03cec0eb68301445102173df3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710660"
---
# <a name="how-to-update-a-visual-studio-extension"></a>如何:更新可視化工作室擴展
您可以使用**擴展和更新**來安裝更新的版本,從而更新系統上的 Visual Studio 擴展。 如果創建擴展的更新版本,則可以通過在 VSIX 清單中增加版本號來將其表示為更新版本。

 當傳入延伸的 VSIX 清單與已安裝的`ID`一個`Version`數位和更高的 數位相同時,將安裝更新。 如果`Version`數位相同或更低,則無法安裝包。 如果`ID`這些值不匹配,則尚未安裝的包將識別為單獨的擴展。

 為了説明防止開發過程中的衝突,我們建議您卸載正在進行的擴展的早期版本,並卸載或禁用任何其他可能衝突的擴展。

## <a name="to-update-an-extension-on-your-system"></a>更新系統上的延伸

1. 在 [工具] **** 功能表上，按一下 [擴充功能和更新] ****。

2. 在左邊窗格中,按下「**更新**」。

3. 在中間窗格中,單擊要安裝的更新。

     更新的擴展的版本號與其他資訊一起顯示在右側窗格中。

4. 在右側窗格的底部,按兩下「**更新**」。

## <a name="to-publish-an-update-of-an-extension"></a>發布延伸的更新

1. 在 Visual Studio 中,打開要更新的擴展的解決方案。 進行更改。

    > [!IMPORTANT]
    > 未簽名的所有用戶擴展不會自動更新。 應始終在擴展中簽名。

2. 在**解決方案資源管理員**中,*開源. 延伸. 清單*。

3. 在清單設計器中,增加 **「版本」** 欄位中的數位值。

4. 保存解決方案並構建它。

5. 將新的 *.vsix*檔(在專案的\*_bin_ 調試資料夾中)上載到[可視化工作室應用商店](https://marketplace.visualstudio.com/vs)網站。

     當具有早期版本的擴展的使用者打開**擴展和更新**時,新版本將顯示在 **「更新**」清單中,前提是該工具設置為自動查找更新。

     您可以在 **「更新」** 窗格(**啟用/ 關閉自動偵測可用更新**)中啟用或關閉自動檢查更新,這會改變 **「工具** > **」來** > **擴充** > **與更新**「中的 **」檢查更新**「設定。

    > [!NOTE]
    > 從 Visual Studio 2015 更新 2 開始,您可以指定(在**工具** > **選項** > **環境** > **擴展和更新**中),是否要自動更新每個使用者擴展、所有使用者擴展或兩者(預設設置)。

## <a name="see-also"></a>另請參閱
- [VSIX 套件的分析](../extensibility/anatomy-of-a-vsix-package.md)
- [尋找及使用視覺化工作室擴充](../ide/finding-and-using-visual-studio-extensions.md)
