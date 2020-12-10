---
title: 使用登錄設定來管理私用資源庫
description: 瞭解如何控制 Visual Studio 資源庫、範例庫或私用資源庫中的控制項、範本和工具的存取權。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d15d845f07310e3efcba6f05538a2207d9c416e4
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994001"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>如何：使用登錄設定管理私用資源庫
如果您是獨立 Shell 擴充功能的系統管理員或開發人員，您可以控制 Visual Studio 資源庫、範例庫或私用資源庫中的控制項、範本和工具的存取權。 若要讓資源庫可供使用或無法使用，請建立 *.pkgdef* 檔案，以描述修改過的登錄機碼及其值。

## <a name="manage-private-galleries"></a>管理私用資源庫
 您可以建立 *.pkgdef* 檔案，以控制在多部電腦上存取資源庫的許可權。 這個檔案的格式必須是下列。

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 索引 `Repositories` 鍵是指要啟用或停用的資源庫。 Visual Studio 資源庫和範例庫會使用下列儲存機制 Guid：

- Visual Studio 圖庫：0F45E408-7995-4375-9485-86B8DB553DC9

- 範例庫： AEB9CB40-D8E6-4615-B52C-27E307F8506C

  `Disabled`值是選擇性的。 預設會啟用資源庫。

  `Priority`值決定了資源庫在 [**選項**] 對話方塊中的列出順序。 Visual Studio 資源庫的優先順序為10，而範例資源庫的優先順序為20。 私用資源庫會從優先級100開始。 如果有數個資源庫具有相同的優先順序值，則它們的出現順序是由其當地語系化屬性的值所決定 `DisplayName` 。

  `Protocol`Atom 型或以 SharePoint 為基礎的資源庫需要此值。

  您 `DisplayName` 必須指定（或兩者皆是 `DisplayNameResourceID` 和兩者 `DisplayNamePackageGuid` ）。 如果已指定 all，則 `DisplayNameResourceID` `DisplayNamePackageGuid` 會使用和配對。

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>使用 .pkgdef 檔案停用 Visual Studio 資源庫
 您可以在 *.pkgdef* 檔案中停用資源庫。 下列專案會停用 Visual Studio 資源庫：

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 下列專案會停用範例庫：

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>另請參閱
- [私用資源庫](../extensibility/private-galleries.md)
