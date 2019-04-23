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
ms.openlocfilehash: 9b78668b0df966de45eb309f068f448809fed8e2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662851"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

會執行 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> 工作，以便在建置 [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] 專案時，將 **\<hostInBrowser />** 項目新增至應用程式資訊清單 (*projectname*.exe.manifest)。  
  
## <a name="task-parameters"></a>工作參數  
  
|參數|說明|  
|---------------|-----------------|  
|`ApplicationManifest`|必要的 **ITaskItem[]** 參數。<br /><br /> 指定要加入 `<hostInBrowser />` 項目的應用程式資訊清單檔案的路徑和名稱。|  
|`HostInBrowser`|必要的 **Boolean** 參數。<br /><br /> 指定是否要修改應用程式資訊清單以包含 **\<hostInBrowser />** 元素。 若為 **true**，**\<entryPoint />** 元素中會包含新的 `<`**hostInBrowser />** 元素。 請注意，元素的包含是累計的：如果 **\<hostInBrowser />** 元素已經存在，就不會移除或覆寫它。 相反地，會建立額外的 **\<hostInBrowser />** 元素。 若為 **false**，則不會修改應用程式資訊清單。|  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[TLA2#tla_xbap#plural](../includes/tla2sharptla-xbapsharpplural-md.md)] 是利用 [!INCLUDE[TLA#tla_clickonce](../includes/tlasharptla-clickonce-md.md)] 部署執行，因此，必須使用支援的部署和應用程式資訊清單加以發行。 [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] 使用 [GenerateApplicationManifest](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) 工作來產生應用程式資訊清單。  
  
 接著，若要設定從瀏覽器裝載應用程式，必須將其他的 **\<hostInBrowser />** 元素加入至應用程式資訊清單，如下列範例所述：  
  
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
  
## <a name="see-also"></a>請參閱  
 [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)   
 [工作參考](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [建置 WPF 應用程式 (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [WPF XAML 瀏覽器應用程式概觀](http://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
