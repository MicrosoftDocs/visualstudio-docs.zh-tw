---
title: 如何：將相依性新增至 VSIX 套件 |Microsoft Docs
description: 瞭解如何設定 VSIX 套件部署，以安裝任何尚未存在於目的電腦上的相依性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb035f9174085667eb229ab5003d8f997eaae84a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953028"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>如何：將相依性新增至 VSIX 套件

您可以設定 VSIX 封裝部署，以安裝任何尚未存在於目的電腦上的相依性。 若要完成這項工作，請將 VSIX 相依性加入 *extension.vsixmanifest* 檔案。

## <a name="to-add-a-dependency"></a>新增相依性

1. 在 **設計** 視圖中開啟 *extension.vsixmanifest* 檔案。 移 **至 [相依** 性] 索引標籤，然後按一下 [ **新增**]。

2. 若要加入已安裝的擴充功能：在 [ **加入新** 的相依性] 對話方塊中，選取 [ **已安裝的延伸** 模組]，然後在 [ **名稱**] 中選取清單上的延伸模組。

3. 若要加入另一個未安裝的 VSIX：在 [ **加入新** 的相依性] 對話方塊中，選取 [檔 **系統上** 的檔案]，然後使用 [ **流覽]** 按鈕選取 VSIX。

## <a name="require-a-specific-visual-studio-release"></a>需要特定的 Visual Studio 版本

例如，如果您的延伸模組需要特定版本的 Visual Studio 2017，則取決於在15.3 中發行的功能，您可以在 VSIX **InstallationTarget** 中指定組建編號。 例如，版本15.3 的組建編號為 ' 15.0.26730.3 '。 您可以在 [這裡](../install/visual-studio-build-numbers-and-release-dates.md)看到版本與組建編號的對應。 請注意，使用版本號碼 ' 15.3 ' 將無法正常運作。

如果您的延伸模組需要15.3 或更高版本，您會將 **InstallationTarget 版本** 宣告為 [15.0.26730.3，16.0) ：

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller 將會偵測舊版 Visual Studio，並通知使用者需要稍後的更新。

## <a name="see-also"></a>另請參閱

- [VSIX 延伸架構1.0 參考](/previous-versions/dd393700(v=vs.110))
- [VSIX 封裝的剖析](../extensibility/anatomy-of-a-vsix-package.md)
- [準備 Windows Installer 部署的擴充功能](../extensibility/preparing-extensions-for-windows-installer-deployment.md)