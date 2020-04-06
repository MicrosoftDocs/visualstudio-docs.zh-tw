---
title: VS 包中的資源 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 493e9834e3d7cf6d82cebb8dd93d5369678c7be0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705607"
---
# <a name="resources-in-vspackages"></a>VSPackage 中的資源
您可以將當地語系化資源嵌入到本機衛星 UI DLL、託管衛星 DLL 或託管 VSPackage 本身中。

 某些資源不能嵌入到 VSPackages 中。 可以嵌入以下託管型態:

- 字串

- 包增入鍵(也是字串)

- 工具視窗圖示

- 編譯的指令表輸出 (CTO) 檔案

- CTO 點陣圖

- 命令列說明

- 關於對話框資料

  託管包中的資源由資源 ID 選擇。 CTO 檔案是一個例外,該檔必須命名為 CTMENU。 CTO 檔案必須在資源表中顯示`byte[]`為 。 所有其他資源項均按類型標識。

  可以使用<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>該[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]屬性指示 該託管資源可用。

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  以這種方式<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>設定指示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在 搜尋資源時應忽略非託管的衛星 DLL,例如,<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>透過使用 。 如果[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]遇到兩個或多個具有相同資源 ID 的資源,則使用它找到的第一個資源。

## <a name="example"></a>範例
 下面的示例是工具視窗圖示的託管表示形式。

```
<data name="1001"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyToolWinIcon.bmp;
     System.Drawing.Bitmap,
     System.Drawing,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

 下面的範例展示如何嵌入必須命名為 CTMENU 的 CTO 位元組。

```
<data name="CTMENU"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyPackage.cto;
     System.Byte[],
     mscorlib,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

## <a name="implementation-notes"></a>實作附註
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]盡可能延遲 VSPackages 的載入。 在 VSPackage 中嵌入 CTO 檔[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的結果是在安裝程式 期間(即生成合併的命令表)期間,必須在記憶體中載入所有此類 VS 包。 無需在 VSPackage 中執行代碼即可從 VSPackage 中提取資源。 VSPackage 此時未初始化,因此性能損失最小。

 在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]安裝程式后從 VSPackage 請求資源時,該包可能已載入和初始化,因此性能損失最小。

## <a name="see-also"></a>另請參閱
- [管理 VSPackage](../../extensibility/managing-vspackages.md)
- [MFC 應用程式中的當地語系化資源：附屬 DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
