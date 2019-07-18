---
title: 網站支援屬性 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a508acaf174e5e4e4b4b615e5f38c600f0669ed
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323390"
---
# <a name="web-site-support-attributes"></a>網站支援屬性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 網站專案可以擴充，提供支援 Web 程式設計語言。 語言必須向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，讓專案範本可以出現在**新的網站**時選取語言 對話方塊。

IronPython Studio 範例包含網站的支援。 此範例包含做為新的 Web 專案的程式碼後置語言註冊 IronPython 的下列屬性類別。

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 這個屬性會放在語言專案。 它將語言新增至網頁中的程式設計語言的清單**語言**列入**新的網站** 對話方塊。 例如，下列程式碼會將 IronPython 加入清單：

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 這個屬性也會設定為指向 [範本] 資料夾的範本路徑。 如需範本資料夾的位置的詳細資訊，請參閱[網站支援範本](../../extensibility/internals/web-site-support-templates.md)。

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 這個屬性會放在語言專案。 它在另一種檔案類型 （主要） 下允許巢狀 （相關） 的一種檔案類型的網站專案中**方案總管 中**。

 例如，下列程式碼指定的 IronPython 程式碼後置檔案與相關的.aspx 檔案。 IronPython Web site 方案中建立新的.aspx 網頁時，會產生新.py 原始程式檔，且會顯示為子節點的.aspx 頁面。

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 這個屬性會放在語言專案套件。 它會選取該語言的 IntelliSense 提供者。

 例如，下列程式碼指定 PythonIntellisenseProvider，它會實作的執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>，應該建立依需求提供語言服務。

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 IVsIntellisenseProject 實作處理參考，並使用程式碼的網頁要求，但未快取時所呼叫的語言編譯器。

## <a name="see-also"></a>另請參閱
- [網站支援](../../extensibility/internals/web-site-support.md)