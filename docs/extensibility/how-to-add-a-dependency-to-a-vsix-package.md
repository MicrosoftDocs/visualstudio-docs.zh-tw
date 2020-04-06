---
title: 如何:向 VSIX 包添加依賴項 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8b350f063c28762edf90edfe71330534451c75d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711071"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>如何:向 VSIX 套件新增相依項

您可以設定 VSIX 套件部署,該部署安裝目標電腦上尚未存在的任何依賴項。 為此,請包括對*來源.擴展.vsixmanifest*檔的 VSIX 依賴項。

## <a name="to-add-a-dependency"></a>新增相依項

1. 在 **「設計」** 檢視中開啟*源.擴展.vsixmanifest*檔案。 跳到 **"依賴項'** 選項卡,然後按**一下 "新建**"。

2. 要添加已安裝的擴展:在 **「添加新依賴項」** 對話方塊中,選擇 **「已安裝副檔名**」,然後,對於 **「名稱**」,請在清單中選擇副檔名。

3. 要新增另一個未安裝的 VSIX:在 **'新增新依賴項'** 對話框中,選擇**檔案系統上的「檔案**」,然後使用 **「瀏覽」** 按鈕選擇 VSIX。

## <a name="require-a-specific-visual-studio-release"></a>需要特定的視覺化工作室版本

例如,如果您的擴展需要 Visual Studio 2017 的特定版本,則它取決於 15.3 中發布的功能,則可以在 VSIX**安裝目標**中指定內部版本號。 例如,版本 15.3 的生成號為"15.0.26730.3"。 你可以[在這裡](../install/visual-studio-build-numbers-and-release-dates.md)看到版本映射以生成數位。 請注意,使用版本號"15.3"將不能正常工作。

如果您的延伸需要 15.3 或更高版本,您將聲明**安裝目標版本**為 [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIX安裝程式將檢測早期版本的 Visual Studio,並通知使用者需要稍後的更新。

## <a name="see-also"></a>另請參閱

- [VSIX 延伸架構 1.0 參考](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [VSIX 套件的分析](../extensibility/anatomy-of-a-vsix-package.md)
- [在 Windows 安裝程式部署準備擴充](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
