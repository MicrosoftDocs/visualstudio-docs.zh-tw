---
title: 新專案生成:在引擎蓋下,第二部分 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8692f2012e5f2733982f04e35a7fed415e49c636
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707014"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>產生新專案︰深入探討，第二部分

在[「新專案生成:罩下」中,第一部分](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)我們看到了**新項目**對話框的填充方式。 假設您選擇了**Visual C++ Windows 應用程式**,填寫了 **「名稱**和**位置**」文本框,然後按一下"確定」。

## <a name="generating-the-solution-files"></a>組建解決方案檔案
 選擇應用程式範本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可指示解壓縮並打開相應的 .vstemplate 檔案,並啟動範本來解釋此檔中的 XML 命令。 這些命令在新解決方案或現有解決方案中創建專案和專案項。

 樣本從保存 .vstemplate 檔的同一 .zip 資料夾中解壓縮源檔(稱為專案範本)。 樣本將這些文件複製到新專案,並相應地對其進行自定義。

### <a name="template-parameter-replacement"></a>樣本參數取代
 當範本將專案樣本複製到新專案時,它將任何範本參數替換為用於自訂檔的字串。 樣本參數是一個特殊的標記,它前面是美元符號,例如,$date$。

 讓我們看一下典型的專案項範本。 提取並檢查程式檔\微軟可視化工作室 8_Common7_IDE_專案範本_CSharp_Windows_1033_Windows應用程式.zip 資料夾中的Program.cs。

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace $safeprojectname$
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

如果創建新的 Windows 應用程式專案名為「簡單」,則範`$safeprojectname$`本將 參數替換為專案的名稱。

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace Simple
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

 有關樣本參數的完整清單,請參閱[樣本參數](../../ide/template-parameters.md)。

## <a name="a-look-inside-a-vstemplate-file"></a>A 看內部 。VSTemplate 檔案
 基本 .vstemplate 檔案具有此格式

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 我們檢視了「\<新項目產生」中的樣本資料>部分[:在胡德下,第一部分](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)。 本節中的標記用於控制 **「新專案」** 對話框的外觀。

 \<範本內容>部分中的標記控制新專案和專案項的生成。 下面是[程式檔\<]微軟可視化工作室 8_Common7_PROJECTTemplate_CSharp_Windows_1033_Windows應用程式.zip 資料夾中的 cwindows 應用程式.vstemplate 檔中的範本內容>部分。

```xml
<TemplateContent>
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">
    <ProjectItem ReplaceParameters="true"
      TargetFileName="Properties\AssemblyInfo.cs">
      AssemblyInfo.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Resources.resx">
      Resources.resx
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
      Settings.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">
      Form1.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Form1.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Program.cs
    </ProjectItem>
  </Project>
</TemplateContent>
```

 專案\<>标记控制项目的生成,\<而專案項>標記控制專案項的生成。 如果參數替換參數為 true,範本將自定義專案檔或項中的所有範本參數。 在這種情況下,除"設置.設置"外,所有專案項都是自定義的。

 TargetFileName 參數指定結果項目檔或項的名稱和相對路徑。 這允許您為專案創建資料夾結構。 如果不指定此參數,專案項的名稱將與專案項範本相同。

 產生的 Windows 應用程式資料夾結構如下所示:

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 樣本中的第一\<個也是唯一的專案>標記如下:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 這指示新專案範本透過複製和自訂樣本項 windows 應用程式.csproj 來創建 Simple.csproj 專案檔。

### <a name="designers-and-references"></a>設計師和參考資料
 您可以在解決方案資源管理員中看到"屬性"資料夾存在並包含預期檔。 但是,專案引用和設計器文件依賴項(如對 Resources.resx Resources.Designer.cs和Form1.csForm1.Designer.cs)又如何呢?  生成時,這些檔將設置在Simple.csproj檔中。

 下面是建立專案引用\<的 Simple.csproj 的 ItemGroup>:

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 您可以看到,這些是解決方案資源管理器中顯示的六個專案引用。 下面是另\<一個專案組>的一節。 為了清楚起見,刪除了許多行代碼。 此部分使Settings.Designer.cs取決於設置設置:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>另請參閱

- [產生新專案︰深入探討，第一部分](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
