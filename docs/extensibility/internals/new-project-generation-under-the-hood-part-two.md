---
title: 新專案產生：在幕後，第二部分 |Microsoft Docs
description: 您可以在建立自己的專案類型時，查看 Visual Studio 整合式開發環境 (IDE) 的詳細資訊， (第2部) 。
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
ms.openlocfilehash: 9e45c9643a1fd2e6dcf9d5520fbb2982736b5109
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668842"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>新專案產生：一探究竟，第二部份

在 [產生新專案的過程中，](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) 我們會在幕後看到 [ **新增專案** ] 對話方塊的填入方式。 讓我們假設您已選取 **Visual c # Windows 應用程式**、填妥 [ **名稱** ] 和 [ **位置** ] 文字方塊，然後按一下 [確定]。

## <a name="generating-the-solution-files"></a>產生方案檔
 選擇應用程式範本會指示 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 將對應的 .vstemplate 檔案解壓縮並開啟，並啟動範本以解讀此檔案中的 XML 命令。 這些命令會在新的或現有的方案中建立專案和專案專案。

 範本解壓縮原始程式檔（稱為專案範本），從保存 .vstemplate 檔案的相同 .ZIP 檔案夾中。 此範本會將這些檔案複製到新的專案，並據以進行自訂。

### <a name="template-parameter-replacement"></a>範本參數取代
 當範本將專案範本複製到新的專案時，它會以字串取代任何範本參數來自訂檔案。 範本參數是一種特殊的標記，前面加上貨幣符號，例如 $date $。

 讓我們看看典型的專案專案範本。 在 Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 資料夾中解壓縮並檢查 Program.cs。

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

如果您建立名為 Simple 的新 Windows 應用程式專案，則範本會將參數取代為 `$safeprojectname$` 專案的名稱。

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

 如需完整的範本參數清單，請參閱 [範本參數](../../ide/template-parameters.md)。

## <a name="a-look-inside-a-vstemplate-file"></a>內的外觀。.Vstemplate 檔案
 基本 .vstemplate 檔案具有此格式

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 我們探討了 \<TemplateData> [新專案產生的一節：在幕後，第一](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)篇。 此區段中的標記是用來控制 [ **新增專案** ] 對話方塊的外觀。

 區段中的標記會 \<TemplateContent> 控制產生新的專案和專案專案。 以下是 \<TemplateContent> \Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 資料夾中 cswindowsapplication .vstemplate 檔案的區段。

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
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
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

 \<Project>標記會控制專案的產生，而 \<ProjectItem> 標記會控制專案專案的產生。 如果參數 ReplaceParameters 為 true，則範本會自訂專案檔或專案中的所有範本參數。 在此情況下，所有專案專案都會自訂，但設定除外。

 TargetFileName 參數會指定所產生專案檔或專案的名稱和相對路徑。 這可讓您建立專案的資料夾結構。 如果您未指定這個引數，專案專案將會具有與專案專案範本相同的名稱。

 產生的 Windows 應用程式資料夾結構如下所示：

 ![Visual Studio 方案總管中 [簡單] 解決方案的 Windows 應用程式資料夾結構的螢幕擷取畫面。](../../extensibility/internals/media/simplesolution.png)

 範本中的第一個和唯一一個 \<Project> 標記會讀取：

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 這會藉由複製和自訂範本專案 windowsapplication 來指示新的專案範本建立簡單的 .csproj 專案檔。

### <a name="designers-and-references"></a>設計工具和參考
 您可以在方案總管中看到 [Properties] 資料夾存在，而且包含預期的檔案。 但是，專案參考和設計工具檔案相依性的相關資訊，例如 Resources.Designer.cs 到 Resources .resx 以及 Form1.Designer.cs 至 Form1.cs？  這些設定會在產生時的簡單 .csproj 檔案中設定。

 以下是 \<ItemGroup> 從建立專案參考的簡單 .csproj：

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

 您可以看到這些都是出現在方案總管中的六個專案參考。 以下是另一個區段 \<ItemGroup> 。 為了清楚起見，已刪除許多行程式碼。 本節會讓 Settings.Designer.cs 相依于設定。設定：

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>另請參閱

- [新專案產生：一探究竟，第一部份](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
