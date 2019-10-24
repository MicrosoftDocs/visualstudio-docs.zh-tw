---
title: Vspackage 中的資源 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07e1e19f802203b9770764330ea894b7d0eb98b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724161"
---
# <a name="resources-in-vspackages"></a>VSPackage 中的資源
您可以將當地語系化的資源內嵌在原生附屬 UI Dll、managed 附屬 Dll 或 managed VSPackage 本身。

 某些資源無法內嵌在 Vspackage 中。 下列受控類型可以內嵌：

- 字串

- 封裝載入索引鍵（也是字串）

- 工具視窗圖示

- 已編譯的命令資料表輸出（CTO）檔案

- CTO 點陣圖

- 命令列說明

- 關於對話方塊資料

  受管理封裝中的資源是由資源識別碼所選取。 例外狀況是 CTO 檔案，必須命名為 CTMENU。 CTO 檔案必須以 `byte[]` 形式出現在資源表格中。 所有其他資源專案都是依類型來識別。

  您可以使用 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 屬性來指示 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可以使用受控資源。

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  以這種方式設定 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 表示 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在搜尋資源（例如，使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>）時，應該忽略非受控附屬 Dll。 如果 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 遇到兩個以上具有相同資源識別碼的資源，則會使用它找到的第一個資源。

## <a name="example"></a>範例
 下列範例是工具視窗圖示的 managed 標記法。

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

 下列範例示範如何內嵌必須命名為 CTMENU 的 CTO byte 陣列。

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

## <a name="implementation-notes"></a>執行附注
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會盡可能延遲載入 Vspackage。 在 VSPackage 中內嵌 CTO 檔案的結果，是 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必須在安裝期間將所有這類 Vspackage 載入記憶體中，這是在建立合併的命令資料表時。 藉由檢查中繼資料，而不需在 VSPackage 中執行程式碼，即可從 VSPackage 中解壓縮資源。 VSPackage 目前並未初始化，因此效能損失最少。

 當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在安裝程式之後從 VSPackage 要求資源時，該封裝可能已經載入並初始化，因此效能損失會降到最低。

## <a name="see-also"></a>請參閱
- [管理 VSPackage](../../extensibility/managing-vspackages.md)
- [MFC 應用程式中的當地語系化資源：附屬 DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
