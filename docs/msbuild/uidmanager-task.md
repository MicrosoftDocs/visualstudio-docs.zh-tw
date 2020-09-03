---
title: UidManager 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37692c541fb2a6e9b2ccf61083dd383e56a79766
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631519"
---
# <a name="uidmanager-task"></a>UidManager 工作

此工作會 <xref:Microsoft.Build.Tasks.Windows.UidManager> 檢查、更新或移除 (uid) 的唯一識別碼，以當地語系化來源 xaml 檔案中包含的所有 xaml 專案。

## <a name="task-parameters"></a>工作參數

| 參數 | 描述 |
|-------------------------| - |
| `IntermediateDirectory` | 選擇性的 **字串** 參數。<br /><br /> 指定用來備份 **MarkupFiles** 參數所指定之來源 XAML 檔案的目錄。 |
| `MarkupFiles` | 必要的 **ITaskItem []** 參數。<br /><br /> 指定要針對 UID 檢查、更新或移除所包含的來源 XAML 檔案。 |
| `Task` | 必要的 **String** 參數。<br /><br /> 指定您想要執行的 UID 管理工作。 有效的選項為 **Check**、**Update** 或 **Remove**。 |

## <a name="example"></a>範例

 下列範例會使用工作 <xref:Microsoft.Build.Tasks.Windows.UidManager> 來檢查指定的來源 XAML 檔案是否包含具有適當 uid 的 xaml 元素。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UidManagerTask">
    <UidManager
      Task="Check"
      MarkupFiles="Page1.xaml;Page2.xaml"
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />
  </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)
- [工作參考](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [如何：將應用程式當地語系化](/dotnet/framework/wpf/advanced/how-to-localize-an-application)