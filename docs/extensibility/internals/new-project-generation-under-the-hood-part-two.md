---
title: 新的專案產生： 在幕後，第二部分 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69174be20a0961a6074650471bcb4b9d1df9fa98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="new-project-generation-under-the-hood-part-two"></a>新的專案產生： 在幕後，第二部分
中[產生新的專案： 下原理，一部份](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)我們可了解如何**新專案**對話方塊方塊會填入。 讓我們假設您已選取**Visual C# Windows 應用程式**、 填寫**名稱**和**位置**文字方塊中，並按下 [確定]。  
  
## <a name="generating-the-solution-files"></a>產生方案檔  
 選擇應用程式範本會指示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]才能解壓縮及開啟對應的.vstemplate 檔案，並啟動來解譯此檔案中的 XML 命令的範本。 這些命令會建立新的或現有方案中的專案和專案項目。  
  
 範本會解壓縮到來源檔案，稱為.zip 資料夾儲存.vstemplate 檔案的項目範本。 範本會將這些檔案複製到新的專案，並據此自訂的方法。  
  
### <a name="template-parameter-replacement"></a>取代範本參數  
 當範本複製到新的專案項目範本時，會取代任何範本參數來自訂此檔案的字串。 樣板參數是特殊的語彙基元，前面有貨幣符號，後面接著例如、 $date$。  
  
 讓我們看看典型的專案項目範本。 擷取並檢查 Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 資料夾中的 Program.cs 中。  
  
```  
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
  
 如果您建立新的 Windows 應用程式專案，名為 Simple 時，範本會取代`$safeprojectname$`參數與專案的名稱。  
  
```  
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
  
 如需完整的範本參數清單，請參閱[範本參數](../../ide/template-parameters.md)。  
  
## <a name="a-look-inside-a-vstemplate-file"></a>深入了解。VSTemplate 檔案  
 基本的.vstemplate 檔案具有這種格式  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 我們探討了\<TemplateData > 一節中[產生新的專案： 下原理，一部份](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)。 本節中的標記用來控制的外觀**新專案** 對話方塊。  
  
 中的標記\<TemplateContent > 區段控制產生新的專案和專案項目。 以下是\<TemplateContent > 從 cswindowsapplication.vstemplate 檔案 \Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 資料夾中的區段。  
  
```  
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
  
 \<專案 > 標記控制的專案，產生和\<專案項目 > 標記控制的專案項目產生。 如果參數 ReplaceParameters 為 true，範本將自訂項目或專案檔中的所有範本參數。 在此情況下，所有專案項目所都自訂，但 Settings.settings 除外。  
  
 TargetFileName 參數會指定產生的專案檔案或項目的相對路徑與名稱。 這可讓您建立專案的資料夾結構。 如果您未指定這個引數，專案項目必須與專案項目範本相同的名稱。  
  
 所產生的 Windows 應用程式資料夾結構看起來像這樣：  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 第一個且唯一\<專案 > 中的範本讀取的標記：  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 這會指示新的專案範本來建立複製和自訂範本的項目 windowsapplication.csproj Simple.csproj 專案檔。  
  
### <a name="designers-and-references"></a>設計工具和參照  
 您可以看到在 [方案總管] 中，確認 [Properties] 資料夾存在，且包含預期的檔案。 但專案相關的項目參考，設計工具檔案相依性，例如 Resources.Designer.cs Resources.resx，來和 Form1.cs 的 Form1.Designer.cs？  這些是 Simple.csproj 檔案中時設定其產生的。  
  
 以下是\<ItemGroup > 從 Simple.csproj 所建立的專案參考：  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 您所見，這些都是出現在 [方案總管] 中的六個專案參考。 以下是從另一個區段\<ItemGroup >。 為了清楚起見，已被刪除的程式碼行數。 這個區段會使 Settings.Designer.cs 視 Settings.settings:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>另請參閱  
 [產生新專案︰深入探討，第一部分](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [ MSBuild](../../msbuild/msbuild.md)