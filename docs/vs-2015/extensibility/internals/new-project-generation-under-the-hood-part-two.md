---
title: 產生新專案︰ 深入來看，第二部分 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5732db4ab36a7e198ee6ebdce185294d3b5bc31
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722485"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>產生新專案︰深入探討，第二部分
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在[產生新專案： Under the Hood、 第一段](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)我們可了解如何**新的專案**就會填入方塊的對話方塊。 假設您已選取**Visual C# Windows 應用程式**、 填入**名稱**並**位置**文字方塊中，然後按下的 [確定]。  
  
## <a name="generating-the-solution-files"></a>產生的方案檔  
 選擇應用程式範本會指示[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]解壓縮和開啟對應的.vstemplate 檔案，並啟動範本，以解譯此檔案中的 XML 命令。 這些命令會建立新的或現有方案中專案和專案項目。  
  
 範本會來源檔案，稱為項目範本，從相同的.vstemplate 檔案的.zip 資料夾解壓縮。 範本會將這些檔案複製到新的專案，並據此自訂它們。 如需專案和項目範本的概觀，請參閱 < [NIB: Visual Studio 範本](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041)。  
  
### <a name="template-parameter-replacement"></a>範本參數取代  
 當範本會複製至新的專案項目範本時，它會取代任何範本參數來自訂檔案的字串。 樣板參數是特殊的語彙基元，為前面和後面接著貨幣符號，例如、 $date$。  
  
 讓我們看看一般專案項目範本。 擷取並檢查在 Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 資料夾中的 Program.cs 中。  
  
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
  
 如果您建立新的 Windows 應用程式專案，名為 Simple 時，範本將會取代`$safeprojectname$`參數與專案的名稱。  
  
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
 基本.vstemplate 檔案的格式  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 我們討論過\<TemplateData > 一節[產生新專案： Under the Hood、 第一段](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)。 在本節中的標記用來控制的外觀**新的專案** 對話方塊。  
  
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
  
 \<專案 > 標記控制的專案時，產生和\<ProjectItem > 標記控制的專案項目產生。 如果參數 ReplaceParameters 為 true，範本將自訂專案檔或項目中的所有範本參數。 在此情況下，所有專案項目所都自訂，但 Settings.settings 除外。  
  
 TargetFileName 參數會指定產生的專案檔或項目的相對路徑與名稱。 這可讓您建立專案的資料夾結構。 如果您未指定這個引數，專案項目必須與專案項目範本同名。  
  
 所產生的 Windows 應用程式資料夾結構看起來像這樣：  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 第一個且唯一\<專案 > 範本讀取的標記：  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 這會指示新的專案範本來建立複製和自訂範本的項目 windowsapplication.csproj Simple.csproj 專案檔。  
  
### <a name="designers-and-references"></a>設計工具和參考  
 您可以看到在 [方案總管] 中，[屬性] 資料夾存在，且包含預期的檔案。 但呢專案參考和設計工具檔案相依性，例如 Resources.resx，到了 Resources.Designer.cs 和 Form1.cs 的 Form1.Designer.cs 嗎？  這些設定在 Simple.csproj 檔案時產生。  
  
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
  
 您所見，這些是出現在 [方案總管] 中的六個專案參考。 以下是從另一個區段\<ItemGroup >。 為了清楚起見已刪除的程式碼行數。 這個區段會使 Settings.Designer.cs Settings.settings 而定：  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>另請參閱  
 [產生新專案︰深入探討，第一部分](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)


