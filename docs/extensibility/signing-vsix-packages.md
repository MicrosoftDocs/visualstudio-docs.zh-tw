---
title: 簽署 VSIX 套件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17179c35496fc19322c5bb951f4d04bc28e5d7bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700094"
---
# <a name="signing-vsix-packages"></a>簽署 VSIX 套件
擴展程式集無需在 Visual Studio 中運行之前進行簽名,但最好這樣做。

 如果要保護擴展並確保其未被篡改,則可以向 VSIX 包添加數位簽名。 對 VSIX 進行簽名後,VSIX 安裝程式將顯示一條消息,指示簽名,以及有關簽名本身的詳細資訊。 如果 VSIX 的內容已被修改,並且 VSIX 尚未再次簽名,則 VSIX 安裝程式將顯示簽名無效。 安裝不會停止,但警告使用者。

> [!IMPORTANT]
> 從 Visual Studio 2015 開始,使用 SHA256 加密以外的任何內容簽名的 VSIX 套件將標識為簽名無效。 VSIX 安裝未被阻止,但會警告使用者。

## <a name="signing-a-vsix-with-vsixsigntool"></a>使用 VSIXSignTool 簽署 VSIX
 在[VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)的 nuget.org 上[,VisualStudioExis 可利用](https://www.nuget.org/profiles/VisualStudioExtensibility)一個 SHA256 加密簽名工具。

#### <a name="to-use-the-vsixsigntool"></a>使用 VSIXSign 工具

1. 將 VSIX 添加到專案。

2. 右鍵按一下解決方案資源管理員的項目節點,選擇 **「新增&#124;管理 NuGet 套件**。  有關 NuGet 和添加 NuGet 套件的詳細資訊,請參閱[NuGet 文件](/NuGet)和[包管理員 UI](/NuGet/Tools/Package-Manager-UI)主題。

3. 從 VisualStudioExex 可性搜尋 VSIXSignTool 並安裝 NuGet 套件。

4. 您現在可以從專案的本地包位置運行 VSIXSignTool。 有關簽名方案(VSIXSignTool.exe /?)請查閱該工具的命令列説明。

   例如,要使用受密碼保護的憑證檔簽署:

   VSIXSignTool.exe 符\<號 /f\<\<憑證檔案> /p 密碼> VSIX 檔案>

## <a name="see-also"></a>另請參閱
- [推出 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)
