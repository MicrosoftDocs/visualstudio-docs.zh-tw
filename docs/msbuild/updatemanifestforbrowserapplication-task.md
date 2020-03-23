---
title: UpdateManifestForBrowserApplication 工作 | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 079eecd6751f168a7beba32eda6d15eda712bd7f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631324"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication 工作

運行<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>該任務是為了在生成 XAML 瀏覽器應用程式 （XBAP） 專案時將**\<主機InBrowser/>** 元素添加到應用程式清單（*\<專案名稱>.exe.manifest）。*

## <a name="task-parameters"></a>工作參數

|參數|描述|
|---------------|-----------------|
|`ApplicationManifest`|必需**的 ITaskItem]** 參數。<br /><br /> 指定要加入 `<hostInBrowser />` 項目的應用程式資訊清單檔案的路徑和名稱。|
|`HostInBrowser`|必要的 **Boolean** 參數。<br /><br /> 指定是否修改應用程式清單以包括**\<主機瀏覽器/>** 元素。 若為 **true**，**\<entryPoint />** 元素中會包含新的 **\<hostInBrowser />** 元素。 元素包含是累積的：如果**\<主機InBrowser/>** 元素已經存在，則不會刪除或覆蓋它。 相反，將創建一個額外的**\<主機瀏覽器/>** 元素。 若為 **false**，則不會修改應用程式資訊清單。|

## <a name="remarks"></a>備註

 XBAP 使用 ClickOnce 部署運行，因此必須使用支援部署和應用程式清單發佈它們。 MSBuild 使用[生成應用程式清單](generateapplicationmanifest-task.md)任務生成應用程式清單。

 然後，要將應用程式佈建為從瀏覽器託管，必須向應用程式清單中添加其他**\<主機InBrowser/>** 元素，如以下示例所示：

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

 當<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>生成 XBAP 專案以添加元素時，`<hostInBrowser />`將運行該任務。

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
- [任務引用](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [任務引用](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML 瀏覽器應用程式概觀](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)