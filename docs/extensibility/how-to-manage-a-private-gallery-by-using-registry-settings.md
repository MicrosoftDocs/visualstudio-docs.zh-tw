---
title: 作法：使用登錄設定管理私人組件庫 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b4f33f7ecf974fe527f814b9febdc861101f1ec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318488"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>作法：使用登錄設定管理私用組件庫
如果您是系統管理員或獨立模式 Shell 擴充功能的開發人員，您可以控制存取權的控制項、 範本和 Visual Studio 組件庫、 範例庫或私用組件庫中的工具。 若要讓資源庫，可以或無法使用，建立 *.pkgdef*描述的已修改的登錄機碼和其值的檔案。

## <a name="manage-private-galleries"></a>管理私人組件庫
 您可以建立 *.pkgdef*檔案來控制多部電腦上的組件庫的存取。 此檔案必須具有下列格式。

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

 `Repositories`索引鍵參考來啟用或停用資源庫。 Visual Studio 組件庫和範例資源庫使用下列存放庫的 Guid:

- Visual Studio 組件庫：0F45E408-7995-4375-9485-86B8DB553DC9

- 範例庫：AEB9CB40-D8E6-4615-B52C-27E307F8506C

  `Disabled`值是選擇性的。 根據預設，會啟用資源庫。

  `Priority`值會決定文件庫中所列的順序**選項** 對話方塊。 Visual Studio 元件庫優先順序 10 和範例庫優先順序 20。 私用組件庫啟動 100 的優先權。 如果數個組件庫中有相同的優先順序值，以其出現的順序由其當地語系化的值決定`DisplayName`屬性。

  `Protocol`是 Atom 或 SharePoint 為基礎的組件庫的必要值。

  請`DisplayName`，或兩者`DisplayNameResourceID`和`DisplayNamePackageGuid`，必須指定。 如果指定 all，則`DisplayNameResourceID`和`DisplayNamePackageGuid`組用。

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>停用使用.pkgdef 檔案 Visual Studio 組件庫
 您可以停用資源庫中的 *.pkgdef*檔案。 下列項目會停用 Visual Studio 組件庫：

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 下列項目會停用範例庫：

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>另請參閱
- [私用組件庫](../extensibility/private-galleries.md)