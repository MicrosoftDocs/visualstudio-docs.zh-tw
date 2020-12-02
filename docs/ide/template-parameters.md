---
title: 專案和項目範本參數
description: 瞭解如何在範本具現化時，使用範本參數取代範本中的值。
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 8e575011f76370083b5a0f461fbb62bbbc839ea3
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479193"
---
# <a name="template-parameters"></a>範本參數

將範本具現化時，您可以取代範本中的值。 若要設定這項功能，請使用「範本參數」。 範本參數可以用來取代範本中的值，例如類別名稱和命名空間。 當使用者新增項目或專案取代這些參數時，範本精靈會在背景中執行。

## <a name="declare-and-enable-template-parameters"></a>宣告和啟用範本參數

範本參數是以 $*parameter*$ 格式來宣告。 例如：

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="enable-parameter-substitution-in-templates"></a>啟用範本中的參數替換

1. 在範本的 *.vstemplate* 檔案中，針對您要啟用參數取代的項目，找出對應的 `ProjectItem` 元素。

1. 將 `ReplaceParameters` 項目的 `ProjectItem` 屬性設定為 `true`。

1. 在適當時，於專案項目的程式碼檔案中納入參數。 例如，下列參數指定用於檔案中命名空間的安全專案名稱：

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>保留的範本參數

下表列出可用於任何範本的保留範本參數：

|參數|描述|
|---------------|-----------------|
|clrversion|通用語言執行平台 (CLR) 的最新版本。|
|ext_*|將 `ext_` 前置詞新增至任何參數，以參考父代範本的變數。 例如： `ext_safeprojectname` 。|
|guid[1-10]|GUID；用來取代專案檔中的專案 GUID。 您最多可以指定 10 個唯一的 GUID (例如，`guid1`)。|
|itemname|正在使用該參數的檔案名稱。|
|machinename|目前的電腦名稱 (例如，Computer01)。|
|projectname|建立專案時，使用者所提供的名稱。|
|registeredorganization|來自 HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization 的登錄機碼值。|
|rootnamespace|目前專案的根命名空間。 這個參數只適用於項目範本。|
|safeitemname|與 `itemname` 相同，但所有不安全的字元和空格都會以底線字元取代。|
|safeitemrootname|與 `safeitemname` 相同。|
|safeprojectname|使用者在建立專案時時提供的名稱，但已移除所有不安全的字元和空格。|
|time|目前的時間，格式為 DD/MM/YYYY 00:00:00。|
|specifiedsolutionname|方案名稱。 若已核取 [建立方案目錄]，則 `specifiedsolutionname` 具有方案名稱。 若未核取 [建立方案目錄]，`specifiedsolutionname` 則為空白。|
|userdomain|目前的使用者網域。|
|username|目前的使用者名稱。|
|webnamespace|目前網站的名稱。 這個參數用於 Web 表單範本，以保證唯一的類別名稱。 如果網站位於 Web 伺服器的根目錄，此範本參數會解析為 Web 伺服器的根目錄。|
|year|目前的年份，格式為 YYYY。|

> [!NOTE]
> 範本參數會區分大小寫。

## <a name="custom-template-parameters"></a>自訂範本參數

除了參數取代期間所使用的預設保留範本參數之外，您也可以指定自己的範本參數和值。 如需詳細資訊，請參閱 [CustomParameters 項目 (Visual Studio 範本)](../extensibility/customparameters-element-visual-studio-templates.md)。

## <a name="example-use-the-project-name-for-a-file-name"></a>範例：檔案名稱使用專案名稱

您可以在 `TargetFileName` 屬性中使用參數，來指定專案項目的變數檔案名稱。

下例會指定可執行檔的名稱使用 `$projectname$` 所指定的專案名稱。

```xml
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>範例：命名空間名稱使用安全的專案名稱

若要在 C# 類別檔案為命名空間使用安全的專案名稱，請使用下列語法：

```csharp
namespace $safeprojectname$
{
    public class Class1
    {
        public Class1()
        { }
    }
}
```

當您參考檔案時，請在專案範本的 *.vstemplate* 檔案中，納入 `ReplaceParameters="true"` 屬性：

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>另請參閱

- [如何：替代範本中的參數](how-to-substitute-parameters-in-a-template.md)
- [自訂範本](../ide/customizing-project-and-item-templates.md)
- [如何：建立專案範本](../ide/how-to-create-project-templates.md)
- [範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
