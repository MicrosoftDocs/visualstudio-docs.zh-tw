---
title: 如何： 更新 Visual Studio 擴充功能 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8bf951215dfb4f6837c157a7b8510fba2d09f140
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500183"
---
# <a name="how-to-update-a-visual-studio-extension"></a>如何： 更新 Visual Studio 擴充功能
您也可以使用您的系統上更新 Visual Studio 擴充功能**擴充功能和更新**安裝更新的版本。 如果您建立延伸模組的更新的版本時，您可以藉由在 VSIX 資訊清單中的版本號碼遞增更新它表示。  
  
 安裝更新時的連入的擴充功能的 VSIX 資訊清單具有相同`ID`安裝和更新版本為`Version`數目。 如果`Version`號碼都是相同或更低，無法安裝此套件。 如果`ID`值不相符，尚未安裝的套件視為個別的擴充功能。  
  
 為了避免衝突，在開發期間，我們建議您解除安裝舊版擴充功能，在進行中，並也解除安裝或停用任何其他可能發生衝突的擴充功能。  
  
## <a name="to-update-an-extension-on-your-system"></a>若要更新您的系統上的擴充功能  
  
1.  在 [工具]  功能表上，按一下 [擴充功能和更新] 。  
  
2.  在左窗格中，按一下**更新**。  
  
3.  在中間窗格中，按一下您想要安裝的更新。  
  
     更新延伸模組的版本號碼會顯示在右窗格中，以及其他資訊。  
  
4.  在右窗格的底部，按一下**更新**。  
  
## <a name="to-publish-an-update-of-an-extension"></a>若要發行的擴充功能更新  
  
1.  在 Visual Studio 中，開啟您想要更新的擴充功能的解決方案。 進行變更。  
  
    > [!IMPORTANT]
    >  不帶正負號不會自動更新所有使用者延伸模組。 您應一律登入您的擴充功能。  
  
2.  在 **方案總管**，開啟*source.extension.manifest*。  
  
3.  在 資訊清單設計工具中，數字值增加**版本**欄位。  
  
4.  將方案儲存並建置專案。  
  
5.  上傳新 *.vsix*檔案 (在 * \bin\Debug\*專案的資料夾) 來[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)網站。  
  
     當具有較早版本的延伸模組的使用者身分開啟**擴充功能和更新**，新的版本會出現在**更新**清單中，前提是此工具設定為自動尋找更新。  
  
     您可以啟用或停用自動檢查更新底部**更新** 窗格 (**啟用/停用自動偵測可用的更新**)，哪些變更**檢查更新**中設定**工具** > **選項** > **環境** >  **擴充功能和更新**。  
  
    > [!NOTE]
    >  從 Visual Studio 2015 Update 2 開始，您可以指定 (在**工具** > **選項** > **環境** >  **擴充功能和更新**) 是否要自動更新每個使用者延伸模組、 所有使用者延伸模組或這兩個 （預設值）。  
  
## <a name="see-also"></a>另請參閱  
 [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)   
 [尋找及使用 Visual Studio 擴充功能](../ide/finding-and-using-visual-studio-extensions.md)