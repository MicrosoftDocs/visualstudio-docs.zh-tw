---
title: HOW TO：新增 vsix 套見的相依性 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ce21c10f1a64bf8edad9181d66b83291d0405c4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902476"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>HOW TO：將相依性加入至 VSIX 封裝

您可以設定安裝中不存在目標電腦上任何相依性的 VSIX 套件部署。 若要達成此目的，包括 VSIX 相依性，以*source.extension.vsixmanifest*檔案。

## <a name="to-add-a-dependency"></a>新增相依性

1. 開啟*source.extension.vsixmanifest*中的檔案**設計**檢視。 移至**相依性**索引標籤，然後按一下**新增**。

2. 若要新增已安裝延伸模組： 在**加入新的相依性**對話方塊中，選取**已安裝擴充功能**，然後針對**名稱**，選取清單上的擴充功能。

3. 若要新增另一個未安裝的 VSIX： 中**加入新的相依性**對話方塊中，選取**在檔案系統上的檔案**，然後使用**瀏覽**按鈕來選取 VSIX。

## <a name="require-a-specific-visual-studio-release"></a>需要特定的 Visual Studio 版本

如果您的延伸模組需要特定版本的 Visual Studio 2017，比方說，這取決於在 15.3 中發行的功能，您可以在您的 VSIX 中指定的組建編號**InstallationTarget**。 例如，版本 15.3 會有 '15.0.26730.3' 組建編號。 您所見的對應版本的組建編號[此處](../install/visual-studio-build-numbers-and-release-dates.md)。 請注意，使用版本號碼 '15.3' 將無法正常運作。

如果您的延伸模組需要 15.3 或更新版本中，您會宣告**InstallationTarget 版本**為 [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller 會偵測舊版的 Visual Studio，並通知使用者，都需要更新版的更新。


## <a name="see-also"></a>另請參閱

 [VSIX 延伸結構描述 1.0 參考](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)   
 [準備 Windows Installer 部署擴充功能](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
