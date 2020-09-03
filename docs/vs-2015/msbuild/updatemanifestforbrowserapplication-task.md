---
title: UpdateManifestForBrowserApplication 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dffa98a8abbf74bd6eee8761d91f09a7c022666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68740225"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

工作 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> 會在建立專案時，執行以將 **\<hostInBrowser />** 專案新增至*projectname*應用程式資訊清單中 (的專案資訊清單) 。 [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)]  
  
## <a name="task-parameters"></a>工作參數  
  
|參數|描述|  
|---------------|-----------------|  
|`ApplicationManifest`|必要的 **ITaskItem []** 參數。<br /><br /> 指定要加入 `<hostInBrowser />` 項目的應用程式資訊清單檔案的路徑和名稱。|  
|`HostInBrowser`|必要的 **Boolean** 參數。<br /><br /> 指定是否要修改應用程式資訊清單以包含 **\<hostInBrowser />** 元素。 若**為 true**，則表示新 `<` 的 **>hostinbrowser/>** 專案包含在 **\<entryPoint />** 元素中。 請注意，元素包含是累計的：如果專案 **\<hostInBrowser />** 已經存在，則不會移除或覆寫它。 相反地， **\<hostInBrowser />** 會建立額外的元素。 若為 **false**，則不會修改應用程式資訊清單。|  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[TLA2#tla_xbap#plural](../includes/tla2sharptla-xbapsharpplural-md.md)] 是利用 [!INCLUDE[TLA#tla_clickonce](../includes/tlasharptla-clickonce-md.md)] 部署執行，因此，必須使用支援的部署和應用程式資訊清單加以發行。 [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] 使用 [GenerateApplicationManifest](/dotnet/api/microsoft.build.tasks.generateapplicationmanifest) 工作來產生應用程式資訊清單。  
  
 然後，若要設定從瀏覽器裝載的應用程式，必須將額外的元素 **\<hostInBrowser />** 加入至應用程式資訊清單，如下列範例所示：  
  
```  
<!--MyXBAPApplication.exe.manifest-->  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly ... >  
    <asmv1:assemblyIdentity ... />  
    <application />  
    <entryPoint>  
      ...  
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />  
    </entryPoint>  
  ...  
/>  
```  
  
 在建置 [!INCLUDE[TLA2#tla_xbap](../includes/tla2sharptla-xbap-md.md)] 專案時，會執行 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> 工作以新增 `<hostInBrowser />` 項目。  
  
## <a name="example"></a>範例  
 下列範例示範如何確定 `<hostInBrowser />` 項目內含於應用程式資訊清單檔中。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"  
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UpdateManifestForBrowserApplicationTask">  
    <UpdateManifestForBrowserApplication  
      ApplicationManifest="MyXBAPApplication.exe.manifest"  
      HostInBrowser="true" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>另請參閱  
 [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)   
 [工作參考](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [ (WPF) 建立 WPF 應用程式 ](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [WPF XAML 瀏覽器應用程式概觀](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
