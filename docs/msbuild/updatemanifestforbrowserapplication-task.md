---
title: UpdateManifestForBrowserApplication 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何執行 UpdateManifestForBrowserApplication 工作，以將 >hostinbrowser 專案新增至應用程式資訊清單。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9e71e11988d4dd853b0f97c745b6d720a45adcdc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961543"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication 工作

<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> **\<hostInBrowser />** 當建立 XAML 瀏覽器應用程式 (XBAP) 專案時，會執行此工作，以將專案新增至應用程式資訊清單 (*\<projectname> .exe. 指令* 清單) 。

## <a name="task-parameters"></a>工作參數

|參數|Description|
|---------------|-----------------|
|`ApplicationManifest`|必要的 **ITaskItem []** 參數。<br /><br /> 指定要加入 `<hostInBrowser />` 項目的應用程式資訊清單檔案的路徑和名稱。|
|`HostInBrowser`|必要的 **Boolean** 參數。<br /><br /> 指定是否要修改應用程式資訊清單以包含 **\<hostInBrowser />** 元素。 若 **為 true**，專案 **\<hostInBrowser />** 中會包含新的元素 **\<entryPoint />** 。 元素包含是累計的：如果專案 **\<hostInBrowser />** 已經存在，則不會移除或覆寫它。 相反地， **\<hostInBrowser />** 會建立額外的元素。 若為 **false**，則不會修改應用程式資訊清單。|

## <a name="remarks"></a>備註

 Xbap 是使用 ClickOnce 部署來執行，因此必須使用支援的部署和應用程式資訊清單加以發行。 MSBuild 會使用 [GenerateApplicationManifest](generateapplicationmanifest-task.md) 工作來產生應用程式資訊清單。

 然後，若要設定要從瀏覽器裝載的應用程式，則 **\<hostInBrowser />** 必須將額外的元素加入至應用程式資訊清單，如下列範例所示：

```xml
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

 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>建立 XBAP 專案以加入專案時，會執行此工作 `<hostInBrowser />` 。

## <a name="example"></a>範例

 下列範例示範如何確定 `<hostInBrowser />` 元素內含於應用程式資訊清單檔中。

```xml
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

- [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)
- [工作參考](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML 瀏覽器應用程式總覽](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)