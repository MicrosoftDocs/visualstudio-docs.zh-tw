---
title: 如何:使用註冊表設置管理專用庫 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2630fc71bea40a4d05e616ae336759ba62431a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710926"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>如何:使用註冊表設置管理專用庫
如果您是獨立命令程式擴展的管理員或開發人員,則可以控制對可視化工作室庫、範例庫或專用庫中的控制項、範本和工具的訪問。 要使庫可用或不可用,請創建一個 *.pkgdef*檔案,用於描述修改後的註冊表項及其值。

## <a name="manage-private-galleries"></a>管理私人畫廊
 您可以創建 *.pkgdef*檔案來控制對多台電腦上的庫的訪問。 此檔必須具有以下格式。

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 該`Repositories`鍵是指要啟用或禁用的庫。 視覺化工作室庫與範例庫使用以下儲存庫 GUID:

- 視覺工作室畫廊 : 0F45E408-7995-4375-9485-86B8DB553DC9

- 樣品庫 : AEB9CB40-D8E6-4615-B52C-27E307F8506C

  該`Disabled`值是可選的。 默認情況下,啟用了庫。

  該`Priority`值確定 **「對話**框中列出庫的順序。 可視化工作室庫具有優先順序 10,示例庫具有優先順序 20。 私人畫廊從優先順序 100 開始。 如果多個庫具有相同的優先順序值,則它們顯示的順序由其本地化`DisplayName`屬性的值決定。

  基於`Protocol`Atom 或基於 SharePoint 的圖庫需要該值。

  必須`DisplayName`指定`DisplayNameResourceID``DisplayNamePackageGuid`或兩者 以及與 。 如果全部指定,則使用`DisplayNameResourceID`和`DisplayNamePackageGuid`對。

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>使用 .pkgdef 檔案禁用視覺化工作室庫
 您可以關閉 *.pkgdef*檔案中的庫。 以下條目禁用視覺工作室庫:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 以下項目關閉範例庫:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>另請參閱
- [私人畫廊](../extensibility/private-galleries.md)
