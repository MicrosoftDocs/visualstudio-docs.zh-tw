---
title: 網站支援屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef75f99480145475278357a552f3ac74c0289800
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703490"
---
# <a name="web-site-support-attributes"></a>網站支援屬性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以擴展網站專案,為 Web 程式設計語言提供支援。 語言必須註冊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]自身,以便專案範本在選擇語言時可以顯示在 **「新建網站」** 對話框中。

IronPython 工作室示例包括網站支援。 該示例包含以下屬性類,用於將IronPython註冊為新Web專案的代碼背後語言。

## <a name="websiteprojectattribute"></a>網站項目屬性
 此屬性放置在語言專案上。 它將語言添加到 **「新建網站」** 對話框中 **「語言**」清單中的 Web 程式設計語言清單中。 例如,以下代碼將 IronPython 加入清單中:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 此屬性還將範本路徑設置以指向範本資料夾。 有關樣本資料夾位置的詳細資訊,請參閱[網站支援樣本](../../extensibility/internals/web-site-support-templates.md)。

## <a name="websiteprojectrelatedfilesattribute"></a>網站項目相關檔案屬性
 此屬性放置在語言專案上。 它允許網站專案嵌套一個文件類型(相關)在**解決方案資源管理員**中的另一個檔案類型(主文件類型)。

 例如,以下代碼指定 IronPython 代碼背後檔與 .aspx 文件相關。 在 IronPython 網站解決方案中建立新的 .aspx Web 頁時,將生成新的 .py 源檔,並顯示為 .aspx 頁的子節點。

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>提供感知提供者屬性
 此屬性放置在語言專案包上。 它為語言選擇 IntelliSense 提供程式。

 例如,以下代碼指定應按需創建 PythonIntellisense Provider<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>的實例來提供語言服務。

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 IVsIntellisense Project 在請求包含代碼的 Web 頁但不緩存時處理引用並調用語言編譯器。

## <a name="see-also"></a>另請參閱
- [網站支援](../../extensibility/internals/web-site-support.md)
