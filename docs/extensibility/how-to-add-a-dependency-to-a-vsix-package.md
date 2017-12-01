---
title: "如何： 加入 VSIX 封裝的相依性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f6f1e4739922a2d73999b36c0dc66e6069a6d6b
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>如何： 將相依性加入至 VSIX 封裝

您可以設定安裝中不存在目標電腦上任何相依性的 VSIX 封裝部署。 若要完成此動作，包含 VSIX 相依性，source.extension.vsixmanifest 檔案。

## <a name="to-add-a-dependency"></a>若要加入相依性

1. 中，開啟 source.extension.vsixmanifest 檔案**設計**檢視。 移至**相依性**索引標籤上，按一下 **新增**。

2. 若要加入已安裝的擴充： 中**加入新的相依性**對話方塊中，選取**安裝擴充功能**，然後針對**名稱**，選取清單上的擴充功能。

3. 若要加入另一個未安裝的 VSIX:: 中**加入新的相依性**對話方塊中，選取**檔案系統上**，然後使用**瀏覽** 按鈕以選取 VSIX。

## <a name="require-a-specific-visual-studio-release"></a>需要特定的 Visual Studio 版本

如果您的擴充功能需要特定版本的 Visual Studio 2017，例如，這取決於 15.3 發行一項功能，您可以在您的 VSIX 中指定的組建編號**InstallationTarget**。 例如，版本 15.3 有 '15.0.26730.3' 組建編號。 您可以看到的組建編號的版本對應[這裡](../install/visual-studio-build-numbers-and-release-dates.md)。 請注意，使用的版本號碼 '15.3' 將無法正常運作。

如果您的擴充功能需要 15.3 或更高版本，您就可以宣告**InstallationTarget 版本**為 [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller 會偵測到舊版的 Visual Studio，並通知使用者需要的更新版的更新。


## <a name="see-also"></a>另請參閱

 [VSIX 擴充功能的結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b) [VSIX 套件的剖析](../extensibility/anatomy-of-a-vsix-package.md)[準備 Windows Installer 部署的擴充功能](../extensibility/preparing-extensions-for-windows-installer-deployment.md)