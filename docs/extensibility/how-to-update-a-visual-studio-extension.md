---
title: "如何： 更新 Visual Studio 擴充功能 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 098d8ca0d779b7a7877c47125017dd2cd6880445
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-update-a-visual-studio-extension"></a>如何： 更新 Visual Studio 擴充功能
您也可以使用您的系統上更新 Visual Studio 擴充功能**擴充功能和更新**安裝更新的版本。 如果您建立擴充功能的更新的版本，您可以為已更新的 VSIX 資訊清單中的版本號碼遞增它表示。  
  
 當連入的擴充功能的 VSIX 資訊清單具有相同的已安裝的更新`ID`以及已安裝的其中一個較高`Version`數目。 如果`Version`數目相同或更低，無法安裝此套件。 如果`ID`值不相符，尚未安裝的封裝視為個別的擴充功能。  
  
 為了避免衝突，在開發期間，我們建議您解除安裝舊版的進行中，擴充功能和也解除安裝或停用任何其他可能有衝突的擴充功能。  
  
### <a name="to-update-an-extension-on-your-system"></a>若要更新您的系統上的擴充功能  
  
1.  在 [工具]  功能表上，按一下 [擴充功能和更新] 。  
  
2.  在左窗格中，按一下 **更新**。  
  
3.  在中間窗格中，按一下您想要安裝的更新。  
  
     更新擴充功能的版本號碼會顯示在右窗格中，以及其他資訊。  
  
4.  在右窗格的底部，按一下 **更新**。  
  
### <a name="to-publish-an-update-of-an-extension"></a>若要發行的擴充功能更新  
  
1.  在 Visual Studio 中，開啟您想要更新的擴充功能的方案。 進行變更。  
  
    > [!IMPORTANT]
    >  不帶正負號所有使用者擴充功能是否不會自動取得都更新。 您應該永遠簽署您的擴充功能。  
  
2.  在**方案總管 中**，開啟 source.extension.manifest。  
  
3.  資訊清單設計工具中，增加數字值**版本**欄位。  
  
4.  將方案儲存並建置該檔案。  
  
5.  新.vsix 檔案 （在專案的 \bin\Debug\ 資料夾） 上傳至[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)網站。  
  
     當具有舊版擴充功能的使用者開啟**擴充功能和更新**，新的版本會出現在**更新**清單，前提是此工具會設定為自動尋找更新。  
  
     您可以啟用或停用自動檢查更新底部**更新**窗格 (**啟用/停用自動偵測可用的更新**)，變更**檢查更新**中設定**工具 / 選項 / 環境 / 擴充功能和更新**。  
  
    > [!NOTE]
    >  從 Visual Studio 2015 Update 2 開始，您可以指定 (在 [工具] / [選項] / [環境] / [延伸模組和更新] 中) 是否要自動更新每個使用者延伸模組、所有使用者延伸模組，或兩者皆自動更新 (預設值)。  
  
## <a name="see-also"></a>另請參閱  
 [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)   
 [尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)
